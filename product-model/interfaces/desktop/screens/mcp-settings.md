---
{
  "entities": [
    {
      "entity": "mcp-settings",
      "shows": [
        "Enabled",
        "Port",
        "Running",
        "Error"
      ],
      "collects": [
        "Enabled",
        "Port"
      ]
    },
    {
      "entity": "mcp-client",
      "shows": [
        "Name",
        "Account scope",
        "All accounts",
        "Draft grant",
        "Organize grant",
        "Send grant",
        "Delete grant",
        "Manage accounts grant",
        "Manage settings grant",
        "Send confirmation",
        "Delete confirmation",
        "Credential"
      ],
      "collects": [
        "Name",
        "Account scope",
        "All accounts",
        "Draft grant",
        "Organize grant",
        "Send grant",
        "Delete grant",
        "Manage accounts grant",
        "Manage settings grant",
        "Send confirmation",
        "Delete confirmation"
      ]
    },
    {
      "entity": "mcp-activity",
      "shows": [
        "Time",
        "Client",
        "Tool",
        "Account",
        "Success"
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/components/dialog/McpSettingsPanel.tsx"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp.go"
    }
  ]
}
---



# MCP settings

Configure the local listener and independently named client connections. A new credential is revealed once as an outcome; recent tool/execution activity is readable here.
