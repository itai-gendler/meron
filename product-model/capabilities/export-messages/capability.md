---
{
  "availability": [
    {
      "place": "desktop"
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

# Export messages

Fetch original EML for selected mail and publish the completed staged export after destination selection. A single-message EML export is saved when fetching/writing/publishing succeeds.
