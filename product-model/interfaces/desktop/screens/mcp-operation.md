---
{
  "entities": [
    {
      "entity": "mcp-operation",
      "shows": [
        "Requesting client",
        "Action",
        "Account",
        "Preview",
        "Approved selection",
        "Expiry",
        "Result",
        "Error"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_operations.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/components/dialog/McpSettingsPanel.tsx"
    }
  ]
}
---


# MCP operation

Review the selected pending request and observe its denial, invalidation or execution result through the trusted local dialog.
