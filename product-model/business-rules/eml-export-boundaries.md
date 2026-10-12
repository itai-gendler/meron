---
{
  "appliesTo": [
    {
      "type": "capability",
      "id": "export-messages"
    },
    {
      "type": "capability",
      "id": "cancel-message-export"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/eml_export.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/emlExport.ts"
    }
  ]
}
---

# Original-message exports publish only prepared supported output

Desktop one-message export is original EML; multiple successful originals form a ZIP. Failed loads can yield partial output, zero successes an error. Save cancellation or export cancellation discards staging before publication.
