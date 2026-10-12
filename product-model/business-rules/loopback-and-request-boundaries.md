---
{
  "appliesTo": [
    {
      "type": "capability",
      "id": "change-mcp-settings"
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
      "id": "rotate-mcp-credential"
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
  ]
}
---

# The optional MCP listener accepts only validated loopback requests

The optional IPv4 loopback listener defaults to port 43827; configured ports are 1024–65535. Current bearer authentication and Host/Origin/path checks precede dispatch. Body size is bounded to 1 MiB. Client names are 1–80 characters, at most 32 clients, with some selected account access/All accounts or management grant. Received content cannot approve an operation.
