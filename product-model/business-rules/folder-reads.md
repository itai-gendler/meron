---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "folder",
      "effect": "reads",
      "facts": [
        "Name",
        "Hierarchy",
        "Role",
        "Unread count"
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

# Scoped clients read folder content

The enabled service follows the target’s owning account to the acting client’s explicit account selection, or admits its All accounts policy. Reading stored compositions does not require Draft grant.
