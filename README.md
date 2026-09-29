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

        # Remove [CODIGO] + " - "
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
    # DESCRIPTION PARSER (CORE)
    # =============================
    def parse_description(self, html):
        soup = BeautifulSoup(html, "html.parser")

        steps = self.extract_gherkin_from_table(soup)
        links = self.extract_links(soup)
        desc_data = self.extract_description_and_obs(soup)

        return {
            "description": desc_data["description"],
            "figma_links": links,
            "steps": steps,
            "observations": desc_data["observations"]
        }

    # =============================
    # GHERKIN (TABLE)
    # =============================
    def extract_gherkin_from_table(self, soup):
        steps = []

        tables = soup.find_all("table")

        for table in tables:
            rows = table.find_all("tr")

            for row in rows:
                cols = row.find_all("td")

                for col in cols:
                    text = col.get_text(" ", strip=True)

                    if text:
                        steps.append(text)

        return steps

    # =============================
    # LINKS (FIGMA)
    # =============================
    def extract_links(self, soup):
        links = []

        for a in soup.find_all("a", href=True):
            href = a["href"]

            if "figma.com" in href:
                links.append(href)

        return links

    # =============================
    # DESCRIPTION + OBS
    # =============================
    def extract_description_and_obs(self, soup):
        description_parts = []
        obs_parts = []

        for p in soup.find_all("p"):
            text = p.get_text(" ", strip=True)

            if not text:
                continue

            if text.lower().startswith("obs"):
                obs_parts.append(text)
            else:
                description_parts.append(text)

        return {
            "description": " ".join(description_parts).strip(),
            "observations": " ".join(obs_parts).strip()
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