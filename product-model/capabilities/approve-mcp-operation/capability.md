---
{
  "availability": [
    {
      "place": "desktop"
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
    }
  ],
  "domain": "mcp-access"
}
---

# Approve MCP operation

Resolve the pending local review as approval, rechecking the originating connection, account scope, action grant, enabled service and expiry before execution. A still-valid captured operation starts; the local review never changes its captured contents/selection.
