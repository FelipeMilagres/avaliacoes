import re
from bs4 import BeautifulSoup


class MergeData:

    def __init__(self):
        # 🔒 Campos permitidos (Kanbanize)
        self.ALLOWED_FIELDS = {
            "QA - Cenário passível de automação?",
            "QA - Como o cenário é executado?",
            "QA - Selecione a(s) unidade(s) de negócio",
            "QA - Qual a prioridade do cenário?"
        }

        # 🎯 Mapeamento definitivo (Kanbanize → LambdaTest)
        self.FIELD_NAME_MAP = {
            "QA - Cenário passível de automação?": "automation_candidate",
            "QA - Como o cenário é executado?": "execution_type",
            "QA - Selecione a(s) unidade(s) de negócio": "business_unit",
            "QA - Qual a prioridade do cenário?": "priority"
        }

        # 🧱 Estrutura padrão obrigatória
        self.DEFAULT_CUSTOM_FIELDS = {
            "automation_candidate": "Não definido",
            "execution_type": "Não informado",
            "business_unit": [],
            "priority": "Média"
        }

    # =====================================================
    # MAIN
    # =====================================================
    def execute(self, data: dict):
        cards = data.get("cards", [])
        tags_map = data.get("tags_map", {})
        custom_fields_map = data.get("custom_fields_map", {})

        result = []

        for card in cards:
            parsed_card = self.parse_card(card, tags_map, custom_fields_map)

            # 🔎 Filtro: apenas cards com tag lambdatest
            if not self.has_lambdatest_tag(parsed_card["tags"]):
                continue

            result.append(parsed_card)

        return result

    # =====================================================
    # CARD PARSER
    # =====================================================
    def parse_card(self, card, tags_map, custom_fields_map):

        parsed_desc = self.parse_description(card.get("description"))

        custom_fields = self.parse_custom_fields(
            card.get("custom_fields", []),
            custom_fields_map
        )

        custom_fields = self.ensure_required_fields(custom_fields)

        return {
            "title": self.clean_title(card.get("title")),
            "description": parsed_desc["description"],
            "figma_links": parsed_desc["figma_links"],
            "steps": parsed_desc["steps"],
            "created_at": card.get("created_at"),
            "tags": self.parse_tags(card.get("tag_ids", []), tags_map),
            "custom_fields": custom_fields
        }

    # =====================================================
    # TITLE
    # =====================================================
    def clean_title(self, title):
        if not title:
            return None

        return re.sub(r"^\[.*?\]\s*-\s*", "", title).strip()

    # =====================================================
    # DESCRIPTION PARSER (HTML → estruturado)
    # =====================================================
    def parse_description(self, html):
        if not html:
            return {
                "description": None,
                "figma_links": [],
                "steps": None
            }

        soup = BeautifulSoup(html, "html.parser")

        sections = {
            "description": [],
            "figma_links": [],
            "steps": []
        }

        current_section = None

        for element in soup.find_all(["p", "li", "strong"]):
            text = element.get_text(strip=True)

            if not text:
                continue

            normalized = text.lower()

            if "descrição" in normalized:
                current_section = "description"
                continue

            elif "figma" in normalized:
                current_section = "figma_links"
                continue

            elif "passo" in normalized:
                current_section = "steps"
                continue

            if current_section:
                if current_section == "figma_links":
                    links = self.extract_links(text)
                    sections[current_section].extend(links)
                else:
                    sections[current_section].append(text)

        return {
            "description": self.join_text(sections["description"]),
            "figma_links": sections["figma_links"],
            "steps": self.join_text(sections["steps"])
        }

    def extract_links(self, text):
        return re.findall(r'https?://\S+', text)

    def join_text(self, items):
        if not items:
            return None
        return "\n".join(items)

    # =====================================================
    # TAGS
    # =====================================================
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
        return "lambdatest" in tags

    # =====================================================
    # CUSTOM FIELDS
    # =====================================================
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

            mapped_name = self.FIELD_NAME_MAP.get(field_name)

            if not mapped_name:
                continue

            resolved_values = self.resolve_field_values(field, field_data)

            if not resolved_values:
                continue

            if len(resolved_values) == 1:
                result[mapped_name] = resolved_values[0]
            else:
                result[mapped_name] = resolved_values

        return result

    # =====================================================
    # GARANTE ESTRUTURA
    # =====================================================
    def ensure_required_fields(self, custom_fields):
        base = self.DEFAULT_CUSTOM_FIELDS.copy()
        base.update(custom_fields)
        return base

    # =====================================================
    # VALUE RESOLUTION
    # =====================================================
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