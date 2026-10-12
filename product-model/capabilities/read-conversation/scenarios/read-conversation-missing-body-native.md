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
      "text": "Request read conversation.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::conversation"
        },
        "android": {
          "place": "android::conversation"
        },
        "ios": {
          "place": "ios::conversation"
        }
      }
    },
    {
      "text": "The selected summary lacks its body and content loading fails.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::conversation"
        },
        "android": {
          "place": "android::conversation"
        },
        "ios": {
          "place": "ios::conversation"
        }
      }
    },
    {
      "text": "The available summary remains with missing/error feedback; a readable full body is not invented.",
      "kind": "product",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::conversation"
        },
        "android": {
          "place": "android::conversation"
        },
        "ios": {
          "place": "ios::conversation"
        }
      },
      "actor": "user"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mail.go#threadRead"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/mail.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/mailFlags.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/thread_read.rs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Mail.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Thread.kt"
    }
  ]
}
---

# Read conversation — missing body native

## Trigger

The selected summary lacks its body and content loading fails.

## Outcome

The available summary remains with missing/error feedback; a readable full body is not invented.
