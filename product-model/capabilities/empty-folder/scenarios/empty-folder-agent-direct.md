---
{
  "kind": "alternative",
  "routes": {
    "mcp": "Mcp"
  },
  "steps": [
    {
      "text": "Request empty mailbox container.",
      "kind": "actor",
      "actor": "mcp-client",
      "entities": [],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      }
    },
    {
      "text": "Valid inputs select the configured direct flow.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      }
    },
    {
      "text": "Retain the normalized request identity and frozen action inputs.",
      "kind": "product",
      "entities": [
        {
          "entity": "mcp-operation",
          "effect": "creates",
          "facts": [
            "Requesting client",
            "Action",
            "Account",
            "Request identity",
            "Argument fingerprint",
            "Preview",
            "Approved selection",
            "Expiry",
            "Result",
            "Error"
          ],
          "to": "Pending approval"
        }
      ],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      },
      "actor": "mcp-client"
    },
    {
      "text": "Begin configured direct execution after current binding and input rechecks.",
      "kind": "product",
      "entities": [
        {
          "entity": "mcp-operation",
          "effect": "changes",
          "facts": [],
          "from": "Pending approval",
          "to": "Running"
        }
      ],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      },
      "actor": "mcp-client"
    },
    {
      "text": "Remove only the frozen approved mail selection.",
      "kind": "product",
      "entities": [
        {
          "entity": "email-message",
          "effect": "removes"
        }
      ],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      },
      "actor": "mcp-client"
    },
    {
      "text": "The retained request executes its frozen inputs and records the resulting terminal state.",
      "kind": "product",
      "entities": [
        {
          "entity": "mcp-operation",
          "effect": "changes",
          "facts": [
            "Result",
            "Preview"
          ],
          "from": "Running",
          "to": "Completed"
        }
      ],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      },
      "actor": "mcp-client"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mail.go#threadRead"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/mail.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/mailFlags.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/thread_read.rs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Mail.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Thread.kt"
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
    }
  ]
}
---


# Empty folder — agent direct

## Trigger

Valid inputs select the configured direct flow.

## Outcome

The retained request executes its frozen inputs and records the resulting terminal state.
