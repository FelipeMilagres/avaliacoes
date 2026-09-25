class MergeData:

    def execute(self, data: dict):
        cards = data.get("cards", [])
        tags_map = data.get("tags_map", {})
        custom_fields_map = data.get("custom_fields_map", {})

        return [
            self._build_card(card, tags_map, custom_fields_map)
            for card in cards
        ]

    # ----------------------------
    # CARD FINAL
    # ----------------------------
    def _build_card(self, card, tags_map, custom_fields_map):
        return {
            "title": card.get("title"),
            "description": card.get("description"),
            "created_at": card.get("created_at"),
            "tags": self._parse_tags(card, tags_map),
            "custom_fields": self._parse_custom_fields(card, custom_fields_map)
        }

    # ----------------------------
    # TAGS
    # ----------------------------
    def _parse_tags(self, card, tags_map):
        tag_ids = card.get("tag_ids", [])

        return [
            self._to_snake_case(tags_map[tag_id])
            for tag_id in tag_ids
            if tag_id in tags_map
        ]

    def _to_snake_case(self, text: str):
        return (
            text.strip()
            .lower()
            .replace(" ", "_")
        )

    # ----------------------------
    # CUSTOM FIELDS
    # ----------------------------
    def _parse_custom_fields(self, card, custom_fields_map):
        result = {}

        for field in card.get("custom_fields", []):
            field_id = field.get("field_id")
            field_meta = custom_fields_map.get(field_id)

            if not field_meta:
                continue

            field_name = field_meta.get("name")

            values = self._resolve_field_values(field, field_meta)

            if values:
                result[field_name] = values

        return result

    def _resolve_field_values(self, field, field_meta):
        values = field.get("values", [])

        # Mapa value_id -> valor real
        allowed_values_map = {
            v["value_id"]: v["value"]
            for v in field_meta.get("allowed_values", [])
        }

        resolved = []

        for v in values:
            value_id = v.get("value_id")

            if value_id in allowed_values_map:
                resolved.append(allowed_values_map[value_id])

        return resolved




from extract.extract_data import ExtractData
from merge.merge_data import MergeData

def main():
    board_id = 12345  # coloca aqui o ID real do seu board

    # 1. Extract
    extractor = ExtractData()
    extracted_data = extractor.execute(board_id)

    print("\n===== EXTRACTED DATA =====")
    print(extracted_data)

    # 2. Merge
    merger = MergeData()
    merged_data = merger.execute(extracted_data)

    print("\n===== MERGED DATA =====")
    for item in merged_data:
        print(item)


if __name__ == "__main__":
    main()