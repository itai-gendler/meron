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

# Retained request execution preserves its originating connection

For execution initiated by the trusted desktop approval flow, the User initiates the Product action. The permission-bearing connection remains the operation's retained Requesting client; approval does not make the User its requester.

The User/configuredBy grant evaluates the actual retained operation selected by the approval call. It requires a current MCP-client configuration entry whose identity and credential hash match the connection captured by that operation. It never selects another client merely because that client can access the account.

The existing related grant continues to govern execution attributed to the originating MCP client. Direct execution remains subject to its existing request-binding and confirmation conditions.

This Rule and the scope/action Rule are AND requirements. Native approval does not bypass either. The configuration-dependent User grant admits only execution initiated through the trusted desktop approval flow for that retained request; it grants no general native mail access.
