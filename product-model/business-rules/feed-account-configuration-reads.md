---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "feed-account",
      "effect": "reads",
      "facts": [
        "Load remote images",
        "Conversation HTML",
        "Unified inclusion",
        "Muted",
        "Paused",
        "Polling interval",
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

# Account managers read feed account configuration

Configuration management is app-wide and independent of content access.
