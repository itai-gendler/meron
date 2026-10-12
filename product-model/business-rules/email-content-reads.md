---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "email-message",
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
      ],
      "contexts": [
        {
          "place": "mcp"
        }
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_tools.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_configuration.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_operations.go"
    }
  ],
  "permits": [
    {
      "related": [
        {
          "verb": "contains",
          "entity": "folder"
        },
        {
          "verb": "has",
          "entity": "mail-account"
        },
        {
          "verb": "has explicit access to",
          "entity": "mcp-client"
        }
      ],
      "when": [
        {
          "entity": "mcp-settings",
          "fact": "Enabled",
          "is": true
        }
      ]
    },
    {
      "actors": [
        "mcp-client"
      ],
      "when": [
        {
          "entity": "mcp-settings",
          "fact": "Enabled",
          "is": true
        },
        {
          "entity": "mcp-client",
          "fact": "All accounts",
          "is": true
        }
      ]
    }
  ]
}
---

# Scoped clients read email message content

The enabled service follows the target’s owning account to the acting client’s explicit account selection, or admits its All accounts policy. Reading stored compositions does not require Draft grant.
