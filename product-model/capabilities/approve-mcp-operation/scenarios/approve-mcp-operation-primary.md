---
{
  "kind": "primary",
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
      "text": "The displayed retained request is Pending approval, unexpired and executable after current request-binding rechecks.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mcp-operation"
        }
      }
    },
    {
      "text": "Start execution of the displayed retained operation.",
      "kind": "product",
      "entities": [
        {
          "entity": "mcp-operation",
          "effect": "changes",
          "from": "Pending approval",
          "to": "Running",
          "facts": []
        }
      ],
      "actor": "user"
    },
    {
      "text": "Record successful execution and clear the executable preview.",
      "kind": "product",
      "entities": [
        {
          "entity": "mcp-operation",
          "effect": "changes",
          "from": "Running",
          "to": "Completed",
          "facts": [
            "Result",
            "Preview"
          ]
        }
      ],
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/components/dialog/McpApprovalDialog.tsx"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp.go#mcpSettings"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp.go#mcpAllows"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_operations.go#resolveOperation"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_operations.go#executeOperation"
    }
  ]
}
---


# Approve mcp operation — primary

## Trigger

The displayed retained request is Pending approval, unexpired and executable after current request-binding rechecks.

## Outcome

The displayed retained operation completes and its executable preview is cleared. Its captured request and originating connection remain unchanged. A completed send records the established SMTP-acceptance outcome.
