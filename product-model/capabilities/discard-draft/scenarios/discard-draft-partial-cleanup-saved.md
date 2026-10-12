---
{
  "kind": "edge",
  "routes": {
    "desktop": "Desktop",
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request discard composition.",
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
      "text": "Some applicable stored copies cannot be removed.",
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
      "text": "Discard the local editable buffer and retain the draft copies whose remote cleanup failed, with the observed cleanup result.",
      "kind": "product",
      "entities": [
        {
          "entity": "draft",
          "effect": "changes",
          "facts": [
            "Stored copies",
            "Save status"
          ]
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


# Discard draft — partial cleanup — saved

## Trigger

The applicable stored composition is Saved. Some applicable stored copies cannot be removed.

## Outcome

The buffer is discarded while failed remote-copy cleanup can leave stored copies.
