---
{
  "kind": "edge",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request send message.",
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
      "text": "Desktop opens its rescue editor after a failed quick reply.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::composer"
        }
      }
    },
    {
      "text": "Captured reply contents seed an editable composition without proving the transport never delivered.",
      "kind": "product",
      "entities": [
        {
          "entity": "outgoing-send",
          "effect": "reads",
          "facts": [
            "Captured contents",
            "Origin",
            "Failure",
            "Retry payload"
          ]
        },
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

# Send message — failed reply rescue

## Trigger

Desktop opens its rescue editor after a failed quick reply.

## Outcome

Captured reply contents seed an editable composition without proving the transport never delivered.
