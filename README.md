Here is a professional, high-end README.md specifically for your Limbu Dictionary API repository.
This version is designed to be the "source of truth" for developers or contributors interacting with your data. It matches your v3 technical standards, emphasizing the specific sorting rules and contribution workflow.
# Limbu Dictionary JSON API (v3)

An open-access, versioned JSON API for the Sirijunga (Limbu) script. This repository serves as the primary data source for the Limbu Dictionary SPA, providing structured linguistic data for Limbu, English, and Nepali.

## 🚀 API Endpoint
Use the following immutable URL to fetch the latest production data with the **v3 cache** standard:

```text
[https://raw.githubusercontent.com/ingsha09/limbu-dictionary-api/main/data.json?v=3](https://raw.githubusercontent.com/ingsha09/limbu-dictionary-api/main/data.json?v=3)

📊 Data Structure
Each entry in the data.json array follows this schema:
{
  "id": "00010",
  "limbu": "ᤀᤀᤡ(ᤒᤠ)",
  "phonetic": "/अइ(बा)/",
  "meaning": {
    "en": "Porcupine",
    "ne": "दुम्सी ।"
  },
  "status": "verified"
}

Schema Definitions:
| Key | Type | Description |
|---|---|---|
| id | String | Unique 5-digit identifier for database indexing. |
| limbu | String | Word in Unicode Sirijunga script. |
| phonetic | String | IPA or Devanagari-based phonetic pronunciation. |
| meaning | Object | Contains en (English) and ne (Nepali) definitions. |
| status | String | Quality flag (verified, pending, or correction_needed). |
🔤 Alphabetical Sorting Logic
To ensure consistent rendering across platforms, data in this API is sorted using a custom Limbu weights array.
Excluded Characters: ᤉ (cha), ᤊ (jha), and ᤚ (ssa) are excluded from primary index filtering to maintain a streamlined dictionary flow.
Sort Order:
ᤀ, ᤁ, ᤂ, ᤃ, ᤄ, ᤅ, ᤆ, ᤇ, ᤈ, ᤋ, ᤌ, ᤍ, ᤎ, ᤏ, ᤐ, ᤑ, ᤒ, ᤓ, ᤔ, ᤕ, ᤖ, ᤗ, ᤘ, ᤙ, ᤛ, ᤜ
🛠 Contribution Workflow
We welcome community contributions. To maintain data integrity, please follow these steps:
1. Adding New Words
Click the + icon in the SPA or open a GitHub Issue with the label add-entry. Provide the Limbu spelling, phonetic, and meanings.
2. Suggesting Edits
If you find a typo or an incorrect translation:
 * Open an Issue.
 * Include the id of the word (e.g., ID: 00010).
 * Describe the required change.
3. Reporting Errors
For technical issues with the JSON structure or character rendering, use the bug report template.
⚖️ License & Usage
This API is provided for linguistic preservation and educational purposes. If you use this data in your own project, please credit the Limbu Dictionary API Project.
Maintained by: ingsha09
Version: 3.0.0 (Sharp UI Sync)


