---
{
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


# MCP activity

Latest 100 recorded outcomes since launch. One recording Rule produces it; mutation Steps do not create log entries explicitly.

## Information kept

- **Time** — The timestamp of the recorded tool/execution outcome.
- **Client** — The client name associated with the recorded outcome.
- **Tool** — The tool whose outcome was recorded.
- **Account** — The targeted account, when the recorded tool or execution has one.
- **Success** — Whether the recorded tool/execution returned success.
