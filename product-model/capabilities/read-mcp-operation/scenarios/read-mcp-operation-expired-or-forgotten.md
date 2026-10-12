---
{
  "kind": "edge",
  "routes": {
    "mcp": "Mcp"
  },
  "steps": [
    {
      "text": "Request read retained request.",
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
      "text": "A still-retained pending request reaches its five-minute expiry when the status call checks it.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      }
    },
    {
      "text": "Expire the retained pending request and clear its preview.",
      "kind": "product",
      "entities": [
        {
          "entity": "mcp-operation",
          "effect": "changes",
          "from": "Pending approval",
          "to": "Expired",
          "facts": [
            "Preview"
          ]
        }
      ],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      },
      "actor": "mcp-client"
    },
    {
      "text": "Return the retained expired status and expiry.",
      "kind": "product",
      "entities": [
        {
          "entity": "mcp-operation",
          "effect": "reads",
          "facts": [
            "Expiry"
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



# Read mcp operation — expired or forgotten

## Trigger

A still-retained pending request reaches its five-minute expiry when the status call checks it.

## Outcome

The status call records Expired, clears the executable preview and returns the retained status and expiry. Expiry itself creates no execution error.
