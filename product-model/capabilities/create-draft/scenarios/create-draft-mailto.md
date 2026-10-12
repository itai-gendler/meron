---
{
  "kind": "alternative",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request create composition.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::composer"
        }
      }
    },
    {
      "text": "Desktop receives a supported mailto URI.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::composer"
        }
      }
    },
    {
      "text": "URI recipients, subject and body seed the opened editor.",
      "kind": "product",
      "entities": [
        {
          "entity": "draft",
          "effect": "creates",
          "facts": [
            "Sending identity",
            "Recipients",
            "Subject",
            "Plain content",
            "HTML content",
            "Reply information",
            "Message identity",
            "Stored copies",
            "Save status"
          ],
          "to": "Editing"
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::composer"
        }
      },
      "actor": "user"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/compose.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/quickReplySend.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/pendingSends.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Compose.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+QuickReply.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/sidecar/dispatch/compose.rs"
    }
  ]
}
---

# Create draft — mailto

## Trigger

Desktop receives a supported mailto URI.

## Outcome

URI recipients, subject and body seed the opened editor.
