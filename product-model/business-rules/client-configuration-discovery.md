---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "mcp-client",
      "effect": "reads",
      "facts": [
        "Manage accounts grant",
        "Manage settings grant"
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
      "self": true,
      "when": [
        {
          "entity": "mcp-settings",
          "fact": "Enabled",
          "is": true
        },
        {
          "fact": "Manage accounts grant",
          "is": true
        }
      ]
    },
    {
      "self": true,
      "when": [
        {
          "entity": "mcp-settings",
          "fact": "Enabled",
          "is": true
        },
        {
          "fact": "Manage settings grant",
          "is": true
        }
      ]
    }
  ]
}
---

# Clients with management grants discover their configuration controls

Discovery reports only the supported sections for the acting client’s app-wide Manage accounts or Manage settings grant; neither confers mail content access.
