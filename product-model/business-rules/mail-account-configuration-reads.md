---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "mail-account",
      "effect": "reads",
      "facts": [
        "Sender name",
        "Connection configuration",
        "Credential availability",
        "Needs reconnect",
        "Certificate trust",
        "Signature",
        "Load remote images",
        "Conversation HTML",
        "Unified inclusion",
        "Muted",
        "Paused",
        "Save sent copy",
        "Order",
        "Avatar",
        "Wallpaper"
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
          "fact": "Manage accounts grant",
          "is": true
        }
      ]
    }
  ]
}
---

# Account managers read nonsecret mail configuration

Manage accounts is app-wide. Configuration disclosure redacts passwords, access/refresh tokens and proxy credentials; connection hosts and ordinary preferences remain nonsecret configuration.
