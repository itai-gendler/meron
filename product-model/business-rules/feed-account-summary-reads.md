---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "feed-account",
      "effect": "reads",
      "facts": [
        "Display name"
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


# Scoped clients and account managers read feed account summaries

Account selection and All accounts admit source summaries. Manage accounts independently admits configuration summaries.

The configuredBy decision uses this acting client’s current retained permission configuration and the actual dispatched read. For mail-tool account summaries, only its explicit account selection or All accounts branch applies. For list_account_configurations, only its Manage accounts branch applies. The configuration branch never admits list_accounts or another mail-summary read outside that client’s mail scope; the scope branches never substitute for Manage accounts on configuration discovery.
