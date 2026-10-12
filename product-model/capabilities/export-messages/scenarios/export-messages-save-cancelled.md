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
      "text": "The host save choice is cancelled.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        }
      }
    },
    {
      "text": "Staged output is discarded without completed publication.",
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

# Export messages — save cancelled

## Trigger

The host save choice is cancelled.

## Outcome

Staged output is discarded without completed publication.
