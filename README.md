To ensure the Limbu Dictionary API is perfectly synchronized with your SPA and the user experience, I have updated the README.md.
Based on my analysis of your data.txt file, the entries currently start with an ID-based or unsorted sequence (e.g., ID 3653 appears before ID 00009). This updated guide now includes a Technical Implementation section that specifically instructs developers on how to use the weight-based sorting logic to ensure the API content is displayed correctly in the UI.
Updated README.md for data.json
# Limbu Dictionary JSON API (v3)

An open-access, versioned JSON API for the Sirijunga (Limbu) script. This repository serves as the primary data source for the Limbu Dictionary SPA, providing structured linguistic data for Limbu, English, and Nepali.

## 🚀 API Endpoint
Use the following immutable URL to fetch the latest production data:
```text
[https://raw.githubusercontent.com/ingsha09/limbu-dictionary-api/main/data.json?v=3](https://raw.githubusercontent.com/ingsha09/limbu-dictionary-api/main/data.json?v=3)

📊 Data Structure
Each entry in the data.json array follows this schema [cite: 1-14]:
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

🔤 Alphabetical Sorting Guide
IMPORTANT: The raw JSON data may not be stored in alphabetical order. To display data correctly in your application, you must implement the following sorting logic using the weights below.
1. Predefined Alphabet Order
Exclude characters ᤉ, ᤊ, and ᤚ. Use this array for indexing:
['ᤀ', 'ᤁ', 'ᤂ', 'ᤃ', 'ᤄ', 'ᤅ', 'ᤆ', 'ᤇ', 'ᤈ', 'ᤋ', 'ᤌ', 'ᤍ', 'ᤎ', 'ᤏ', 'ᤐ', 'ᤑ', 'ᤒ', 'ᤓ', 'ᤔ', 'ᤕ', 'ᤖ', 'ᤗ', 'ᤘ', 'ᤙ', 'ᤛ', 'ᤜ']
2. Implementation Logic (JavaScript Example)
const limbuAlphabet = [...]; // Use array above

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

🛠 Contribution Workflow
We welcome community contributions to expand this dataset.
 * Add Entry: Open a GitHub Issue with the label add-entry.
 * [cite_start]Suggest Edits: Use the id of the word (e.g., ID: 00010) to suggest corrections.
 * Reporting: For technical issues with the JSON structure, use the bug report template.
Maintained by: ingsha09
Version: 3.0.0 (Sharp UI Sync)


