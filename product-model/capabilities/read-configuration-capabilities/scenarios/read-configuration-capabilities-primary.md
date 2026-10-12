---
{
  "kind": "primary",
  "routes": {
    "mcp": "Mcp"
  },
  "steps": [
    {
      "text": "Request read configuration capabilities.",
      "kind": "actor",
      "actor": "mcp-client",
      "entities": [],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      }
    },
    {
      "text": "The current request resolves the published supported configuration controls.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      }
    },
    {
      "text": "Return the supported configuration controls for the current request. Supported account/app controls are discoverable; discovery does not expose arbitrary bridge commands.",
      "kind": "product",
      "entities": [
        {
          "entity": "mcp-client",
          "effect": "reads",
          "facts": [
            "Manage accounts grant",
            "Manage settings grant"
          ]
        }
      ],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      },
      "actor": "mcp-client"
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

# Read configuration capabilities — primary

## Trigger

The current request resolves the published supported configuration controls.

## Outcome

Return the supported configuration controls for the current request. Supported account/app controls are discoverable; discovery does not expose arbitrary bridge commands.
