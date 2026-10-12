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
      "text": "The displayed request is still retained and Pending approval when its five-minute expiry is reached and checked.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mcp-operation"
        }
      }
    },
    {
      "text": "Expire the checked pending request and clear its executable preview.",
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


# Approve mcp operation — expired or invalidated — expired

## Trigger

The displayed request is still retained and Pending approval when its five-minute expiry is reached and checked.

## Outcome

The retained request becomes Expired and its executable preview is cleared. The frozen mail action does not execute.
