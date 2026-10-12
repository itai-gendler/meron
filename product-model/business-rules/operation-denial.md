---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "mcp-operation",
      "effect": "changes",
      "contexts": [
        {
          "place": "desktop::mcp-operation"
        }
      ],
      "to": "Denied"
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
        "user"
      ]
    }
  ]
}
---

# The local user denies a pending reviewed operation

The trusted local UI can deny a Pending approval request without performing its mail mutation; denial is not exposed as an MCP tool.
