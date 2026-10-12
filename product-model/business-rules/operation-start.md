---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "mcp-operation",
      "effect": "changes",
      "to": "Running"
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
      "target": "desktop/frontend/src/components/dialog/McpApprovalDialog.tsx"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp.go#mcpSettings"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp.go#mcpAllows"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_operations.go#resolveOperation"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_operations.go#executeOperation"
    }
  ],
  "permits": [
    {
      "related": [
        {
          "verb": "is targeted by",
          "entity": "mail-account"
        },
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
        },
        {
          "entity": "mcp-client",
          "fact": "Send grant",
          "is": true
        },
        {
          "fact": "Action",
          "is": "send_message"
        }
      ]
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
          "fact": "Send grant",
          "is": true
        },
        {
          "entity": "mcp-client",
          "fact": "All accounts",
          "is": true
        },
        {
          "fact": "Action",
          "is": "send_message"
        }
      ]
    },
    {
      "related": [
        {
          "verb": "is targeted by",
          "entity": "mail-account"
        },
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
        },
        {
          "entity": "mcp-client",
          "fact": "Delete grant",
          "is": true
        },
        {
          "fact": "Action",
          "is": "delete_permanently"
        }
      ]
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
          "fact": "Delete grant",
          "is": true
        },
        {
          "entity": "mcp-client",
          "fact": "All accounts",
          "is": true
        },
        {
          "fact": "Action",
          "is": "delete_permanently"
        }
      ]
    },
    {
      "related": [
        {
          "verb": "is targeted by",
          "entity": "mail-account"
        },
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
        },
        {
          "entity": "mcp-client",
          "fact": "Delete grant",
          "is": true
        },
        {
          "fact": "Action",
          "is": "empty_trash"
        }
      ]
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
          "fact": "Delete grant",
          "is": true
        },
        {
          "entity": "mcp-client",
          "fact": "All accounts",
          "is": true
        },
        {
          "fact": "Action",
          "is": "empty_trash"
        }
      ]
    },
    {
      "actors": [
        "user"
      ],
      "configuredBy": "mcp-client",
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

# Retained requests start only with the originating client's current scope and action grant

For native approval, evaluate the current MCP-client configuration entry matched to the actual retained operation's originating connection, including its captured credential binding. Use that entry's current Account scope, All accounts and action grant, not the permission values captured when the request was created.

The retained operation's Account must be explicitly selected by that client or covered by its All accounts setting. Its original action must still have the corresponding grant:

- send_message requires Send grant.
- delete_permanently requires Delete grant.
- empty_trash requires Delete grant.

These requirements apply when the User initiates execution through the trusted desktop approval flow. The User is the approval Actor, not a replacement permission-bearing client.

Existing MCP-client grants continue to govern client-attributed execution. Configured direct execution retains its existing no-confirmation conditions.

This Rule and the originating-connection Rule are AND requirements. Passing one cannot compensate for failing the other. Missing, credential-mismatched, out-of-scope or no-longer-permitted originating configuration never starts the retained operation.

The retained request must still be Pending approval and unexpired when checked. Execution uses the captured send contents or exact deletion snapshot; approval does not replace them.
