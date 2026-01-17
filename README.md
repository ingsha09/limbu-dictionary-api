# Limbu Dictionary JSON API (v3)

An open-access, versioned JSON API for the Sirijunga (Limbu) script. This repository serves as the primary data source for the Limbu Dictionary SPA, providing structured linguistic data for Limbu, English, and Nepali translations.

---

## 🚀 API Endpoint
Use the following immutable URL to fetch the latest production data:

```text
https://raw.githubusercontent.com/ingsha09/limbu-dictionary-api/main/data.json
```

---

## 📊 Data Structure
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
  "group": "AA",
  "status": "verified"
}
```

### Data Schema (v3)

| Key            | Type   | Required | Description                                                                 |
|-----------------|--------|----------|-----------------------------------------------------------------------------|
| `id`           | String | Yes      | Unique 5-digit identifier (e.g., "00010").                                 |
| `limbu`        | String | Yes      | Word in Unicode Sirijunga script. Used as the primary sort key.            |
| `phonetic`     | String | Yes      | Devanagari or IPA pronunciation guide.                                     |
| `group`        | String | No       | Internal classification code (e.g., "AA", "BI").                          |
| `meaning.en`   | String | Yes      | English definition/translation.                                            |
| `meaning.ne`   | String | Yes      | Nepali definition/translation.                                             |
| `status`       | String | Yes      | Data quality flag: `verified`, `pending`, or `correction_needed`.          |

---


### Predefined Alphabet Order

Exclude characters `ᤉ`, `ᤊ`, and `ᤚ`. Use the following array for indexing:

```javascript
['ᤀ', 'ᤁ', 'ᤂ', 'ᤃ', 'ᤄ', 'ᤅ', 'ᤆ', 'ᤇ', 'ᤈ', 'ᤋ', 'ᤌ', 'ᤍ', 'ᤎ', 'ᤏ', 'ᤐ', 'ᤑ', 'ᤒ', 'ᤓ', 'ᤔ', 'ᤕ', 'ᤖ', 'ᤗ', 'ᤘ', 'ᤙ', 'ᤛ', 'ᤜ']
```

### Implementation Logic (JavaScript Example)

```javascript
const limbuAlphabet = ['ᤀ', 'ᤁ', 'ᤂ', 'ᤃ', 'ᤄ', 'ᤅ', 'ᤆ', 'ᤇ', 'ᤈ', 'ᤋ', 'ᤌ', 'ᤍ', 'ᤎ', 'ᤏ', 'ᤐ', 'ᤑ', 'ᤒ', 'ᤓ', 'ᤔ', 'ᤕ', 'ᤖ', 'ᤗ', 'ᤘ', 'ᤙ', 'ᤛ'];

function sortLimbu(data) {
    return data.sort((a, b) => {
        const idxA = limbuAlphabet.indexOf(a.limbu.charAt(0));
        const idxB = limbuAlphabet.indexOf(b.limbu.charAt(0));
        
        // Handle characters not in the primary index
        if (idxA !== idxB) {
            return (idxA === -1 ? 1 : idxB === -1 ? -1 : idxA - idxB);
        }
        // Secondary sort for same starting character
        return a.limbu.localeCompare(b.limbu);
    });
}
```

---

## 🛠 Contribution Workflow

We welcome community contributions to expand this dataset. Below are the guidelines:

1. **Add Entry**: Open a GitHub Issue with the label `add-entry`.
2. **Suggest Edits**: Use the ID of the word (e.g., `ID: 00010`) to suggest corrections.
3. **Report Technical Issues**: For issues with the JSON structure, use the bug report template.

---

## 🧑‍💻 Maintainer & Version

- **Maintained by**: [ingsha09](https://github.com/ingsha09)
