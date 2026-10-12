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

# Cancel message export

Cancel the active export before publication and discard staged output. Cancellation prevents the staged result from replacing the destination; already published output is past this cancellation boundary.
