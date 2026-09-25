import re


class MergeData:

    ALLOWED_FIELDS = {
        "QA - Cenário passível de automação?",
        "QA - Como o cenário é executado?",
        "QA - Selecione a(s) unidade(s) de negócio",
        "QA - Qual a prioridade do cenário?"
    }

    def execute(self, data: dict):
        cards = data.get("cards", [])
        tags_map = data.get("tags_map", {})
        custom_fields_map = data.get("custom_fields_map", {})

        result = []

        for card in cards:
            parsed = self.parse_card(card, tags_map, custom_fields_map)

            # 🔴 FILTRO: só cards com tag lambdatest
            if "lambdatest" not in parsed["tags"]:
                continue

            result.append(parsed)

        return result

    # =========================
    # CARD PARSER
    # =========================
    def parse_card(self, card, tags_map, custom_fields_map):
        return {
            "title": self.clean_title(card.get("title")),
            "description": card.get("description"),
            "created_at": card.get("created_at"),
            "tags": self.parse_tags(card.get("tag_ids", []), tags_map),
            "custom_fields": self.parse_custom_fields(
                card.get("custom_fields", []),
                custom_fields_map
            )
        }

    # =========================
    # TITLE
    # =========================
    def clean_title(self, title):
        if not title:
            return None

        # remove [COD-000]
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

            # 🔴 FILTRO de campos relevantes
            if field_name not in self.ALLOWED_FIELDS:
                continue

            clean_name = self.normalize_field_name(field_name)

            # mapa value_id → value
            allowed_values = {
                v["value_id"]: v["value"]
                for v in field_data.get("allowed_values", [])
            }

            values = field.get("values", [])

            resolved_values = [
                allowed_values.get(v["value_id"])
                for v in values
                if v.get("value_id") in allowed_values
            ]

            # 🔴 trata multi-select
            if not resolved_values:
                continue
            elif len(resolved_values) == 1:
                result[clean_name] = resolved_values[0]
            else:
                result[clean_name] = resolved_values

        return result

    def normalize_field_name(self, name):
        return name.replace("QA - ", "").strip()