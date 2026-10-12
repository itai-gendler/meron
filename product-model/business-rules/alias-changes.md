---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "account-alias",
      "effect": "changes",
      "facts": [
        "Address",
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
    }
  ],
  "permits": [
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
      ]
    }
  ]
}
---

# Account managers change sending aliases

Replacing the complete configured alias list can create, change and remove sending identities. This configuration does not verify ownership of an external address.
