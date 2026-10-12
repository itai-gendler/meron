---
{
  "kind": "primary",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request revoke client connection.",
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
      "text": "An existing configured client is selected for revocation.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mcp-settings"
        }
      }
    },
    {
      "text": "Remove the selected configured client and close its pending access paths. Its credential no longer authenticates subsequent calls; dispatched account setup is not rolled back.",
      "kind": "product",
      "entities": [
        {
          "entity": "mcp-client",
          "effect": "removes"
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


# Revoke mcp client — primary

## Trigger

An existing configured client is selected for revocation.

## Outcome

Remove the selected configured client and close its pending access paths. Its credential no longer authenticates subsequent calls; dispatched account setup is not rolled back.

## Edge cases

- With no pending requests, no operation state changes; running or terminal requests are not cancelled by this save. A port request that leaves the port unchanged does not perform a save.
