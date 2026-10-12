---
{
  "kind": "primary",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request change service preferences.",
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
      "text": "A supported enabled state or integer loopback port between 1024 and 65535 is submitted and service persistence/binding succeeds.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mcp-settings"
        }
      }
    },
    {
      "text": "Persist enabled/port configuration and start, stop or rebind the optional loopback listener. The configured service state and actual listener result are observable.",
      "kind": "product",
      "entities": [
        {
          "entity": "mcp-settings",
          "effect": "changes",
          "facts": [
            "Enabled",
            "Port",
            "Running",
            "Error"
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


# Change mcp settings — primary

## Trigger

A supported enabled state or integer loopback port between 1024 and 65535 is submitted and service persistence/binding succeeds.

## Outcome

Persist enabled/port configuration and start, stop or rebind the optional loopback listener. The configured service state and actual listener result are observable.

## Edge cases

- With no pending requests, no operation state changes; running or terminal requests are not cancelled by this save. A port request that leaves the port unchanged does not perform a save.
