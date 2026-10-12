---
{
  "kind": "primary",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request browse recent tool log.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mcp-settings"
        }
      }
    },
    {
      "text": "The recent in-memory dispatched tool/execution entries are available.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mcp-settings"
        }
      }
    },
    {
      "text": "Read the latest recorded client/tool/account execution outcomes since launch. Recent activity is readable; it is bounded to 100 entries and is not a durable audit archive.",
      "kind": "product",
      "entities": [
        {
          "entity": "mcp-activity",
          "effect": "reads",
          "facts": [
            "Time",
            "Client",
            "Tool",
            "Account",
            "Success"
          ]
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::mcp-settings"
        }
      },
      "actor": "user"
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

# Browse mcp activity — primary

## Trigger

The recent in-memory dispatched tool/execution entries are available.

## Outcome

Read the latest recorded client/tool/account execution outcomes since launch. Recent activity is readable; it is bounded to 100 entries and is not a durable audit archive.
