---
{
  "kind": "edge",
  "routes": {
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request move message.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::mailbox"
        },
        "ios": {
          "place": "ios::mailbox"
        }
      }
    },
    {
      "text": "Mobile chooses another-account column.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::mailbox"
        },
        "ios": {
          "place": "ios::mailbox"
        }
      }
    },
    {
      "text": "The command omits destination account and resolves against the source account; a source-account move, no-op or failure is possible rather than proven other-account delivery.",
      "kind": "product",
      "entities": [],
      "contexts": {
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

# Move message — mobile target discrepancy

## Trigger

Mobile chooses another-account column.

## Outcome

The command omits destination account and resolves against the source account; a source-account move, no-op or failure is possible rather than proven other-account delivery.
