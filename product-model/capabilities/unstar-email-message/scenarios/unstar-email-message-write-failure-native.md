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
      "text": "Request unstar mail.",
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
      "text": "The selected Starred flag mutation fails on its server/store route.",
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
      "text": "The caller retains its mutation error or reconciles preceding flags; clearing Starred is not established as successful. Earlier successful work can remain.",
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


# Unstar email message — write failure native

## Trigger

The selected Starred flag mutation fails on its server/store route.

## Outcome

The caller retains its mutation error or reconciles preceding flags; clearing Starred is not established as successful. Earlier successful work can remain.
