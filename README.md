# Limbu Dictionary JSON API (v3)

An open-access, versioned JSON API for the Sirijunga (Limbu) script. This repository serves as the primary data source for the Limbu Dictionary SPA, providing structured linguistic data for Limbu, English, and Nepali languages.

---

## 🚀 API Overview

### API Endpoint
Use the following immutable URL to fetch the latest production data with the **v3 cache** standard:

```text
https://raw.githubusercontent.com/ingsha09/limbu-dictionary-api/main/data.json?v=3
```

### 📊 Data Structure

Each entry in the `data.json` array follows this schema:

```json
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
```

#### Schema Definitions

| Key      | Type   | Description                                          |
|----------|--------|------------------------------------------------------|
| `id`     | String | Unique 5-digit identifier for database indexing.     |
| `limbu`  | String | Word in Unicode Sirijunga script.                    |
| `phonetic` | String | IPA or Devanagari-based phonetic pronunciation.    |
| `meaning`| Object | Contains `en` (English) and `ne` (Nepali) definitions. |
| `status` | String | Quality flag (e.g., `verified`, `pending`, or `correction_needed`). |

---

## 🔤 Alphabetical Sorting Logic

Data in this API is sorted using a custom Limbu weights array to ensure consistent rendering across platforms.

### Excluded Characters
The following characters are **excluded** from the primary index:
- ᤉ (cha)
- ᤊ (jha)
- ᤚ (ssa)

### Sort Order
The custom sorting order is defined as:

```text
ᤀ, ᤁ, ᤂ, ᤃ, ᤄ, ᤅ, ᤆ, ᤇ, ᤈ, ᤋ, ᤌ, ᤍ, ᤎ, ᤏ, ᤐ, ᤑ, ᤒ, ᤓ, ᤔ, ᤕ, ᤖ, ᤗ, ᤘ, ᤙ, ᤛ, ᤜ
```

---

## 🛠 Contribution Workflow

We welcome community contributions! To maintain data integrity, please follow these steps:

### Adding New Words
1. Click the "+" icon in the SPA or open a GitHub Issue with the label `add-entry`.
2. Provide the following details:
   - Limbu spelling
   - Phonetic representation
   - English and Nepali meanings

### Suggesting Edits
If you find a typo or an incorrect translation:
1. Open an Issue.
2. Include the `id` of the word (e.g., ID: `00010`).
3. Describe the required changes.

### Reporting Errors
For technical issues with the JSON structure or character rendering:
- Use the bug report template in this repository.

---

## ⚖️ License & Usage

This API is provided for linguistic preservation and educational purposes. If you use this data in your project, please credit the Limbu Dictionary API Project.

---

### Maintainer
- **GitHub Username**: [ingsha09](https://github.com/ingsha09)

---

## 📌 Version
**Current version**: 3.0.0

---
