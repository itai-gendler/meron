---
{
  "kind": "primary",
  "routes": {
    "desktop": "Desktop",
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request refresh messages.",
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
      "text": "The selected mail source has usable connection configuration and synchronization succeeds.",
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
      "text": "Check the selected account, synchronize mailbox container/headers/flags and fetch supported content through its configured connection. Obtained mailbox information is cached and presented; remote errors do not become guaranteed live completeness.",
      "kind": "product",
      "entities": [
        {
          "entity": "email-message",
          "effect": "creates",
          "facts": [
            "Location",
            "Message identity",
            "Sender",
            "Recipients",
            "Reply information",
            "Subject",
            "Date",
            "Plain content",
            "HTML content",
            "Thread information",
            "Unread",
            "Starred",
            "Body availability"
          ]
        },
        {
          "entity": "mail-account",
          "effect": "changes",
          "facts": [
            "Credential availability",
            "Needs reconnect"
          ]
        }
      ],
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

# Refresh messages — primary

## Trigger

The selected mail source has usable connection configuration and synchronization succeeds.

## Outcome

Check the selected account, synchronize folders/headers/flags and fetch supported content through its configured connection. Obtained mailbox information is cached and presented; remote errors do not become guaranteed live completeness.
