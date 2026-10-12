---
{
  "kind": "alternative",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request export messages.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        }
      }
    },
    {
      "text": "Several original messages are exported.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        }
      }
    },
    {
      "text": "Successful original EML entries are assembled into a ZIP and published through the host save operation.",
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
          "place": "desktop::mailbox"
        }
      },
      "actor": "user"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/eml_export.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/emlExport.ts"
    }
  ]
}
---

# Export messages — batch

## Trigger

Several original messages are exported.

## Outcome

Successful original EML entries are assembled into a ZIP and published through the host save operation.
