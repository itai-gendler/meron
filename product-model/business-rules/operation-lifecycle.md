---
{
  "appliesTo": [
    {
      "type": "capability",
      "id": "approve-mcp-operation"
    },
    {
      "type": "capability",
      "id": "deny-mcp-operation"
    },
    {
      "type": "capability",
      "id": "read-mcp-operation"
    },
    {
      "type": "capability",
      "id": "change-mcp-settings"
    },
    {
      "type": "capability",
      "id": "revoke-mcp-client"
    },
    {
      "type": "capability",
      "id": "rotate-mcp-credential"
    },
    {
      "type": "capability",
      "id": "add-mcp-client"
    },
    {
      "type": "capability",
      "id": "change-mcp-client"
    },
    {
      "type": "capability",
      "id": "remove-account"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp.go"
    },
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
      "target": "desktop/mcp_mutations.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_operations.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/mcp_mail.rs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp.go#save"
    }
  ]
}
---



# Retained operation states remain bounded to the current process

Pending requests expire after five minutes when checked; records are retained for up to one hour in process memory. Denial/expiry/cancellation clear executable previews. Configuration/credential changes can invalidate pending access. Execution records Completed/Failed and refreshes mail even after uncertainty. Restart is not durable history. Already dispatched account setup is not rolled back by later revocation.

A successful MCP configuration save cancels every pending operation, including requests belonging to other configured clients, and clears their previews. This applies to client creation/editing, revocation, rotation, enablement and an actual port change. Running/terminal records retain their outcomes; failed saves do not publish the new configuration.

Desktop account removal also cancels pending work when explicit-scope pruning produces a successful configuration save; if no explicit selection changes, no such save occurs.
