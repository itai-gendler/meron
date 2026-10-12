---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "mcp-operation",
      "effect": "reads",
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
          "verb": "requests",
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
    }
  ]
}
---

# Requesting clients read their retained operation results

The requesting current client connection reads its retained status/result/expiry. Credential binding is checked against the captured request. Original mutation grant is not required merely to poll; continued account scope is governed separately.
