---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "account-alias",
      "effect": "reads",
      "facts": [
        "Address",
        "Display name"
      ],
      "contexts": [
        {
          "place": "mcp"
        }
      ]
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
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_configuration.go#configurationAccounts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/types.go#Account"
    }
  ]
}
---

# Account managers read configured sending aliases

The app-wide Manage accounts grant admits alias addresses and display names returned with account configuration. A mail-scope grant alone does not admit this configuration read. Native selected-account settings retain ordinary local access.
