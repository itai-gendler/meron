---
{
  "kind": "validation",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request approve retained request.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mcp-operation"
        }
      }
    },
    {
      "text": "The retained pending request is still unexpired, but its originating connection or current configuration fails the execution recheck.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mcp-operation"
        }
      }
    },
    {
      "text": "Close the invalidated pending request and clear its executable preview.",
      "kind": "product",
      "entities": [
        {
          "entity": "mcp-operation",
          "effect": "changes",
          "from": "Pending approval",
          "to": "Cancelled",
          "facts": [
            "Preview"
          ]
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::mcp-operation"
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


# Approve mcp operation — expired or invalidated

## Trigger

The retained pending request is still unexpired, but its originating connection or current configuration fails the execution recheck.

## Outcome

The retained request becomes Cancelled and its executable preview is cleared. The frozen mail action does not execute.
