---
{
  "kind": "primary",
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
      "text": "The retained request identifier resolves in the current process and returns its status/result.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      }
    },
    {
      "text": "Read the retained operation identified by the retained request and current credential. The retained status, expiry and result/error are returned.",
      "kind": "product",
      "entities": [
        {
          "entity": "mcp-operation",
          "effect": "reads",
          "facts": [
            "Requesting client",
            "Action",
            "Account",
            "Request identity",
            "Expiry",
            "Result",
            "Error"
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

# Read mcp operation — primary

## Trigger

The retained request identifier resolves in the current process and returns its status/result.

## Outcome

Read the retained operation identified by the retained request and current credential. The retained status, expiry and result/error are returned.
