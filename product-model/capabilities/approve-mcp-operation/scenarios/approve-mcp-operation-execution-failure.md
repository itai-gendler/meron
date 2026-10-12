---
{
  "kind": "edge",
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
      "text": "Executing the frozen approved action fails.",
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
      "text": "Record the execution result and error and clear the executable preview.",
      "kind": "product",
      "entities": [
        {
          "entity": "mcp-operation",
          "effect": "changes",
          "from": "Running",
          "to": "Failed",
          "facts": [
            "Result",
            "Error",
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

# Approve mcp operation — execution failure

## Trigger

Executing the frozen approved action fails.

## Outcome

The retained operation becomes Failed, records its result and error, and clears its executable preview. Its captured request and originating connection remain unchanged. An execution error does not roll back already completed effects or establish that an uncertain send was not accepted.
