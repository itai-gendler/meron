---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "mail-account",
      "effect": "reads",
      "facts": [
        "Address",
        "Display name",
        "Provider"
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_tools.go#mcpRegister"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_configuration.go#registerConfigurationTools"
    }
  ],
  "permits": [
    {
      "related": [
        {
          "verb": "has explicit access to",
          "entity": "mcp-client"
        }
      ],
      "when": [
        {
          "entity": "mcp-settings",
          "fact": "Enabled",
          "is": true
        }
      ],
      "configuredBy": "mcp-client"
    },
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
          "fact": "All accounts",
          "is": true
        }
      ],
      "configuredBy": "mcp-client"
    },
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
      ],
      "configuredBy": "mcp-client"
    }
  ]
}
---


# Scoped clients and account managers read mail account summaries

The enabled MCP service returns mail summaries within the acting client’s configured account selection or All accounts policy. Manage accounts independently admits configuration summaries; it does not grant mail content.

The configuredBy decision uses this acting client’s current retained permission configuration and the actual dispatched read. For mail-tool account summaries, only its explicit account selection or All accounts branch applies. For list_account_configurations, only its Manage accounts branch applies. The configuration branch never admits list_accounts or another mail-summary read outside that client’s mail scope; the scope branches never substitute for Manage accounts on configuration discovery.
