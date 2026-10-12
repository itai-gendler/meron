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
      "text": "The selected account-aware conversation resolves with available message content.",
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
      "text": "Resolve the selected account-aware conversation and load its supported message page, headers, bodies and available attachment metadata. The conversation is readable as chat or traditional mail over the same messages; MCP returns bounded pages without marking them read.",
      "kind": "product",
      "entities": [
        {
          "entity": "email-message",
          "effect": "reads",
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
          "entity": "attachment",
          "effect": "reads",
          "facts": [
            "Filename",
            "Media type",
            "Size",
            "Content availability",
            "Content location",
            "Inline identity"
          ]
        }
      ],
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

# Read conversation — primary native

## Trigger

The selected account-aware conversation resolves with available message content.

## Outcome

Resolve the selected account-aware conversation and load its supported message page, headers, bodies and available attachment metadata. The conversation is readable as chat or traditional mail over the same messages; MCP returns bounded pages without marking them read.
