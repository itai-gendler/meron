---
{
  "kind": "alternative",
  "routes": {
    "desktop": "Desktop",
    "android": "Android",
    "ios": "Ios"
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
        },
        "android": {
          "place": "android::composer"
        },
        "ios": {
          "place": "ios::composer"
        }
      }
    },
    {
      "text": "Full reply is opened from existing mail.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::composer"
        },
        "android": {
          "place": "android::composer"
        },
        "ios": {
          "place": "ios::composer"
        }
      }
    },
    {
      "text": "Derived reply recipients, threading and content seed the editor; own addresses/aliases influence recipient derivation.",
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
        },
        "android": {
          "place": "android::composer"
        },
        "ios": {
          "place": "ios::composer"
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

# Create draft — reply

## Trigger

Full reply is opened from existing mail.

## Outcome

Derived reply recipients, threading and content seed the editor; own addresses/aliases influence recipient derivation.
