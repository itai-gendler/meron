---
{
  "kind": "edge",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request export messages.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        }
      }
    },
    {
      "text": "Some original content loads fail or none succeed.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        }
      }
    },
    {
      "text": "Successful entries can form a partial export; zero successes yields an error instead of empty-success publication.",
      "kind": "product",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        }
      },
      "actor": "user"
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

# Export messages — partial or empty

## Trigger

Some original content loads fail or none succeed.

## Outcome

Successful entries can form a partial export; zero successes yields an error instead of empty-success publication.
