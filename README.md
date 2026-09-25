import re


class MergeData:

    def __init__(self):
        self.ALLOWED_FIELDS = {
            "QA - Cenário passível de automação?",
            "QA - Como o cenário é executado?",
            "QA - Selecione a(s) unidade(s) de negócio",
            "QA - Qual a prioridade do cenário?"
        }

        self.DEFAULT_CUSTOM_FIELDS = {
            "Cenário passível de automação?": None,
            "Como o cenário é executado?": None,
            "Selecione a(s) unidade(s) de negócio": [],
            "Qual a prioridade do cenário?": None
        }

    # =========================
    # ENTRYPOINT
    # =========================
    def execute(self, data: dict):
        cards = data.get("cards", [])
        tags_map = data.get("tags_map", {})
        custom_fields_map = data.get("custom_fields_map", {})

        result = []

        for card in cards:
            parsed_card = self.parse_card(card, tags_map, custom_fields_map)

            # 🔴 FILTRO: só cards com tag lambdatest
            if not self.has_lambdatest_tag(parsed_card["tags"]):
                continue

            result.append(parsed_card)

        return result

    # =========================
    # CARD PARSER
    # =========================
    def parse_card(self, card, tags_map, custom_fields_map):
        custom_fields = self.parse_custom_fields(
            card.get("custom_fields", []),
            custom_fields_map
        )

        # 🔴 GARANTE estrutura fixa dos 4 campos
        custom_fields = self.ensure_required_fields(custom_fields)

        return {
            "title": self.clean_title(card.get("title")),
            "description": card.get("description"),
            "created_at": card.get("created_at"),
            "tags": self.parse_tags(card.get("tag_ids", []), tags_map),
            "custom_fields": custom_fields
        }

    # =========================
    # TITLE
    # =========================
    def clean_title(self, title):
        if not title:
            return None

        return re.sub(r"\[.*?\]\s*", "", title).strip()

    # =========================
    # TAGS
    # =========================
    def parse_tags(self, tag_ids, tags_map):
        tags = []

        for tag_id in tag_ids:
            tag_name = tags_map.get(tag_id)

            if not tag_name:
                continue

            tags.append(self.to_snake_case(tag_name))

        return tags

    def to_snake_case(self, text):
        return text.lower().replace(" ", "_")

    def has_lambdatest_tag(self, tags):
        return any("lambdatest" in tag for tag in tags)

    # =========================
    # CUSTOM FIELDS
    # =========================
    def parse_custom_fields(self, card_custom_fields, custom_fields_map):
        result = {}

        for field in card_custom_fields:
            field_id = field.get("field_id")
            field_data = custom_fields_map.get(field_id)

            if not field_data:
                continue

            field_name = field_data.get("name")

            # 🔴 FILTRO
            if field_name not in self.ALLOWED_FIELDS:
                continue

            clean_name = self.normalize_field_name(field_name)

            resolved_values = self.resolve_field_values(field, field_data)

            if not resolved_values:
                continue

            # multi-select
            if len(resolved_values) == 1:
                result[clean_name] = resolved_values[0]
            else:
                result[clean_name] = resolved_values

        return result

    # =========================
    # GARANTE CAMPOS PADRÃO
    # =========================
    def ensure_required_fields(self, custom_fields):
        base = self.DEFAULT_CUSTOM_FIELDS.copy()
        base.update(custom_fields)
        return base

    # =========================
    # VALUE RESOLUTION
    # =========================
    def resolve_field_values(self, field, field_data):
        allowed_values_map = self.build_allowed_values_map(field_data)
        values = field.get("values", [])

        resolved = []

        for v in values:
            value_id = v.get("value_id")

            if value_id in allowed_values_map:
                resolved.append(allowed_values_map[value_id])

        return resolved

    def build_allowed_values_map(self, field_data):
        return {
            v["value_id"]: v["value"]
            for v in field_data.get("allowed_values", [])
        }

    # =========================
    # NORMALIZATION
    # =========================
    def normalize_field_name(self, name):
        return name.replace("QA - ", "").strip()