---
{
  "acts": "external",
  "kind": "system",
  "relations": [
    {
      "entity": "mcp-operation",
      "verb": "requests",
      "cardinality": "one-to-many"
    },
    {
      "entity": "mail-account",
      "verb": "has explicit access to",
      "cardinality": "many-to-many"
    },
    {
      "entity": "feed-account",
      "verb": "has explicit access to",
      "cardinality": "many-to-many"
    }
  ],
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


# MCP client

A configured external system connection that initiates MCP requests. Its credential, scope and independent grants are configured locally, replaced or revoked without asserting a particular human or AI harness identity.

## Information kept

- **Name** — The user-supplied label for this configured client connection.
- **Account scope** — The explicitly selected existing account connections.
- **All accounts** — Whether account access includes future or re-added accounts.
- **Draft grant** — Whether the connection can create/replace stored drafts.
- **Organize grant** — Whether the connection can change email flags and location.
- **Send grant** — Whether the connection can request sending.
- **Delete grant** — Whether the connection can request permanent email deletion.
- **Manage accounts grant** — Whether app-wide account configuration management is granted.
- **Manage settings grant** — Whether app-wide supported preference management is granted.
- **Send confirmation** — Whether requested sending waits for the local review dialog.
- **Delete confirmation** — Whether requested permanent deletion waits for local review.
- **Credential** — The issued connection credential; only its hash is retained after the one-time plaintext reveal.
