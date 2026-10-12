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

# Browse MCP activity

Read the latest recorded client/tool/account execution outcomes since launch. Recent activity is readable; it is bounded to 100 entries and is not a durable audit archive.
