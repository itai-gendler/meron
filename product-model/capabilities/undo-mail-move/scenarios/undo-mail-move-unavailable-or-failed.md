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
      "text": "Request undo mail move.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        },
        "android": {
          "place": "android::mailbox"
        },
        "ios": {
          "place": "ios::mailbox"
        }
      }
    },
    {
      "text": "Undo information is missing or reverse movement fails.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        },
        "android": {
          "place": "android::mailbox"
        },
        "ios": {
          "place": "ios::mailbox"
        }
      }
    },
    {
      "text": "Successful exact restoration is not reported.",
      "kind": "product",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        },
        "android": {
          "place": "android::mailbox"
        },
        "ios": {
          "place": "ios::mailbox"
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

# Undo mail move — unavailable or failed

## Trigger

Undo information is missing or reverse movement fails.

## Outcome

Successful exact restoration is not reported.
