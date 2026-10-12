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
      "text": "Request print conversation.",
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
      "text": "Full conversation paging completes without non-progress and the host accepts printing.",
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
      "text": "Load every page of the selected conversation, deduplicate and order messages, then prepare them for host printing without read marking. The print request includes the complete obtained conversation, not just the currently loaded reading page.",
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
            "Content availability"
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
      "target": "desktop/frontend/src/lib/printMail.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/PrintMail.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/iosMain/kotlin/jp/nonbili/meron/ui/PrintMail.ios.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/androidMain/kotlin/jp/nonbili/meron/ui/PrintMail.android.kt"
    }
  ]
}
---

# Print conversation — primary

## Trigger

Full conversation paging completes without non-progress and the host accepts printing.

## Outcome

Load every page of the selected conversation, deduplicate and order messages, then prepare them for host printing without read marking. The print request includes the complete obtained conversation, not just the currently loaded reading page.
