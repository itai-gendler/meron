---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "feed-account",
      "effect": "changes",
      "facts": [
        "Display name",
        "Load remote images",
        "Conversation HTML",
        "Unified inclusion",
        "Muted",
        "Paused"
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

# Account managers change supported feed preferences

Only meaningful supported account preferences apply to subscription accounts. Polling interval, server credentials, media paths and arbitrary preference keys are outside this tool contract.
