---
{
  "singleton": true,
  "domain": "mcp-access",
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
  ]
}
---


# MCP settings

Disabled by default; reflects the inspected listener/configuration outcomes. Collection sizes used for capacity validation are not new permission facts.

## Information kept

- **Enabled** — Whether local MCP access is configured on.
- **Port** — The configured loopback listener port.
- **Running** — The observed local listener running state.
- **Error** — The error reported for listener startup, binding or service configuration.
