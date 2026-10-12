---
{
  "kind": "primary",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request add client connection.",
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
      "text": "The client name is 1–80 characters, fewer than 32 clients exist and a usable account or management configuration is selected.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mcp-settings"
        }
      }
    },
    {
      "text": "Create the named client, retain scope/grants/confirmation choices and the new credential hash, and reveal the plaintext credential once. The configured connection can use its selected contract; the plaintext credential cannot later be reread.",
      "kind": "product",
      "entities": [
        {
          "entity": "mcp-client",
          "effect": "creates",
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
            "Delete confirmation",
            "Credential"
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


# Add mcp client — primary

## Trigger

The client name is 1–80 characters, fewer than 32 clients exist and a usable account or management configuration is selected.

## Outcome

Create the named client, retain scope/grants/confirmation choices and the new credential hash, and reveal the plaintext credential once. The configured connection can use its selected contract; the plaintext credential cannot later be reread.

## Edge cases

- With no pending requests, no operation state changes; running or terminal requests are not cancelled by this save. A port request that leaves the port unchanged does not perform a save.
