import re
from bs4 import BeautifulSoup


class MergeData:

    def __init__(self):
        # Campos permitidos (Kanbanize)
        self.ALLOWED_FIELDS = {
            "QA - Cenário passível de automação?",
            "QA - Como o cenário é executado?",
            "QA - Selecione a(s) unidade(s) de negócio",
            "QA - Qual a prioridade do cenário?"
        }

        # Estrutura obrigatória
        self.DEFAULT_CUSTOM_FIELDS = {
            "Cenário passível de automação?": None,
            "Como o cenário é executado?": None,
            "Selecione a(s) unidade(s) de negócio": [],
            "Qual a prioridade do cenário?": None
        }

    # =============================
    # MAIN
    # =============================
    def execute(self, data: dict):
        cards = data.get("cards", [])
        tags_map = data.get("tags_map")
        custom_fields_map = data.get("custom_fields_map")

        result = []

        for card in cards:
            parsed_card = self.parse_card(card, tags_map, custom_fields_map)

            # FILTRO: apenas LambdaTest
            if not self.has_lambdatest_tag(parsed_card["tags"]):
                continue

            result.append(parsed_card)

        return result

    # =============================
    # PARSE CARD
    # =============================
    def parse_card(self, card, tags_map, custom_fields_map):

        description_data = self.parse_description(card.get("description", ""))

        custom_fields = self.parse_custom_fields(
            card.get("custom_fields", []),
            custom_fields_map
        )

        custom_fields = self.ensure_required_fields(custom_fields)

        return {
            "title": self.clean_title(card.get("title")),
            "description": description_data["description"],
            "figma_links": description_data["figma_links"],
            "steps": description_data["steps"],
            "observations": description_data["observations"],
            "created_at": card.get("created_at"),
            "tags": self.parse_tags(card.get("tag_ids", []), tags_map),
            "custom_fields": custom_fields
        }

    # =============================
    # TITLE
    # =============================
    def clean_title(self, title):
        if not title:
            return None

        return re.sub(r"\[.*?\]\s*-\s*", "", title).strip()

    # =============================
    # TAGS
    # =============================
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

    # =============================
    # DESCRIPTION PARSER (CORRIGIDO)
    # =============================
    def parse_description(self, html):
        soup = BeautifulSoup(html, "html.parser")

        description_parts = []
        observations_parts = []
        steps = []
        links = []

        found_steps_section = False
        found_table = False

        for element in soup.find_all(["p", "a", "table"]):

            # -----------------------------
            # LINKS (FIGMA)
            # -----------------------------
            if element.name == "a" and element.get("href"):
                href = element["href"]
                if "figma.com" in href:
                    links.append(href)

            # -----------------------------
            # DETECTA "PASSO A PASSO"
            # -----------------------------
            if element.name == "p":
                text_lower = element.get_text(" ", strip=True).lower()

                if "passo a passo" in text_lower:
                    found_steps_section = True
                    continue

            # -----------------------------
            # STEPS (TABLE)
            # -----------------------------
            if element.name == "table":
                found_table = True

                rows = element.find_all("tr")

                for row in rows:
                    cols = row.find_all("td")

                    for col in cols:
                        text = col.get_text(" ", strip=True)

                        if text:
                            steps.append(text)

                continue

            # -----------------------------
            # DESCRIPTION (ANTES DO STEP)
            # -----------------------------
            if element.name == "p" and not found_steps_section:
                text = element.get_text(" ", strip=True)

                if text:
                    description_parts.append(text)

            # -----------------------------
            # OBS (DEPOIS DA TABLE)
            # -----------------------------
            elif element.name == "p" and found_table:
                text = element.get_text(" ", strip=True)

                if text:
                    observations_parts.append(text)

        return {
            "description": " ".join(description_parts).strip(),
            "figma_links": links,
            "steps": steps,
            "observations": " ".join(observations_parts).strip()
        }

    # =============================
    # CUSTOM FIELDS
    # =============================
    def parse_custom_fields(self, card_custom_fields, custom_fields_map):
        result = {}

        for field in card_custom_fields:
            field_id = field.get("field_id")
            field_data = custom_fields_map.get(field_id)

            if not field_data:
                continue

            field_name = field_data.get("name")

            if field_name not in self.ALLOWED_FIELDS:
                continue

            clean_name = self.normalize_field_name(field_name)

            resolved_values = self.resolve_field_values(field, field_data)

            if not resolved_values:
                continue

            if len(resolved_values) == 1:
                result[clean_name] = resolved_values[0]
            else:
                result[clean_name] = resolved_values

        return result

    def ensure_required_fields(self, custom_fields):
        base = self.DEFAULT_CUSTOM_FIELDS.copy()
        base.update(custom_fields)
        return base

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

    def normalize_field_name(self, name):
        return name.replace("QA - ", "").strip()