---
{
  "kind": "primary",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request deny retained request.",
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
      "text": "The displayed retained request is Pending approval.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mcp-operation"
        }
      }
    },
    {
      "text": "Resolve the pending trusted local review as denial and discard its executable preview/continuation. The operation is Denied and its mail mutation does not execute.",
      "kind": "product",
      "entities": [
        {
          "entity": "mcp-operation",
          "effect": "changes",
          "facts": [
            "Preview"
          ],
          "from": "Pending approval",
          "to": "Denied"
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


# Deny mcp operation — primary

## Trigger

The displayed retained request is Pending approval.

## Outcome

Resolve the pending trusted local review as denial and discard its executable preview/continuation. The operation is Denied and its mail mutation does not execute.
