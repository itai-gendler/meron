---
{
  "kind": "primary",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request rotate mcp credential.",
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
      "text": "An existing configured client receives a successfully retained replacement credential.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mcp-settings"
        }
      }
    },
    {
      "text": "Generate/retain the replacement credential hash and reveal its plaintext once. The old credential is invalid and the new credential is available for configuration.",
      "kind": "product",
      "entities": [
        {
          "entity": "mcp-client",
          "effect": "changes",
          "facts": [
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


# Rotate mcp credential — primary

## Trigger

An existing configured client receives a successfully retained replacement credential.

## Outcome

Generate/retain the replacement credential hash and reveal its plaintext once. The old credential is invalid and the new credential is available for configuration.

## Edge cases

- With no pending requests, no operation state changes; running or terminal requests are not cancelled by this save. A port request that leaves the port unchanged does not perform a save.
