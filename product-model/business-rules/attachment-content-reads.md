---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "attachment",
      "effect": "reads",
      "facts": [
        "Filename",
        "Media type",
        "Size",
        "Content availability",
        "Content location",
        "Inline identity"
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
      "related": [
        {
          "verb": "has",
          "entity": "email-message"
        },
        {
          "verb": "contains",
          "entity": "folder"
        },
        {
          "verb": "has",
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
        }
      ]
    },
    {
      "related": [
        {
          "verb": "has",
          "entity": "draft"
        },
        {
          "verb": "has",
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
          "fact": "All accounts",
          "is": true
        }
      ]
    }
  ]
}
---

# Scoped clients read available attachment contents

Available cached bytes follow the owning mail/composition account scope. Cache-key/path and size checks are validation, not additional entitlement.
