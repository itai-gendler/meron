---
{
  "kind": "alternative",
  "routes": {
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request print conversation.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "ios": {
          "place": "ios::conversation"
        }
      }
    },
    {
      "text": "iOS receives the print request.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "ios": {
          "place": "ios::conversation"
        }
      }
    },
    {
      "text": "Plain-content preparation is handed to its host without desktop HTML-printing parity.",
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

# Print conversation — ios plain

## Trigger

iOS receives the print request.

## Outcome

Plain-content preparation is handed to its host without desktop HTML-printing parity.
