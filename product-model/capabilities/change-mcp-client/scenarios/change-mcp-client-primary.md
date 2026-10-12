---
{
  "kind": "primary",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request change client connection.",
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
      "text": "The configured client still exists and its scope/grant/confirmation settings save succeeds.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mcp-settings"
        }
      }
    },
    {
      "text": "Persist the selected client scope, grant and confirmation edits and invalidate pending work as implemented. Subsequent calls use the changed current configuration rather than an initialized connection snapshot.",
      "kind": "product",
      "entities": [
        {
          "entity": "mcp-client",
          "effect": "changes",
          "facts": [
            "Name",
            "Account scope",
            "All accounts",
            "Draft grant",
            "Organize grant",
            "Send grant",
            "Delete grant",
            "Manage accounts grant",
            "Manage settings grant",
            "Send confirmation",
            "Delete confirmation"
          ]
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::mcp-settings"
        }
      },
      "actor": "user"
    },
    {
      "text": "Cancel every currently pending retained request and clear its executable preview after the configuration save.",
      "kind": "product",
      "actor": "user",
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
      ]
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
      "target": "desktop/mcp.go#save"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_operations.go#cancelPending"
    }
  ]
}
---


# Change mcp client — primary

## Trigger

The configured client still exists and its scope/grant/confirmation settings save succeeds.

## Outcome

Persist the selected client scope, grant and confirmation edits and invalidate pending work as implemented. Subsequent calls use the changed current configuration rather than an initialized connection snapshot.

## Edge cases

- With no pending requests, no operation state changes; running or terminal requests are not cancelled by this save. A port request that leaves the port unchanged does not perform a save.
