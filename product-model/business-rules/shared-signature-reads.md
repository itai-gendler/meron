---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "app-settings",
      "effect": "reads",
      "facts": [
        "Signature"
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
          "fact": "Manage settings grant",
          "is": true
        }
      ]
    }
  ]
}
---

# Settings managers read the shared signature

The app-wide Manage settings grant independently admits the supported signature operation, with HTML/type/size validation.
