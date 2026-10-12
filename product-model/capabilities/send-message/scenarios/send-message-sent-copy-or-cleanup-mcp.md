---
{
  "kind": "edge",
  "routes": {
    "mcp": "Mcp"
  },
  "steps": [
    {
      "text": "Request send message.",
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
      "text": "SMTP acceptance succeeds but later Sent append/cache or consumed-copy cleanup fails.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      }
    },
    {
      "text": "Retain the frozen send request.",
      "kind": "product",
      "actor": "mcp-client",
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      },
      "entities": [
        {
          "entity": "mcp-operation",
          "effect": "creates",
          "to": "Pending approval",
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
          ]
        }
      ]
    },
    {
      "text": "Begin the configured send after current request and connection rechecks.",
      "kind": "product",
      "actor": "mcp-client",
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      },
      "entities": [
        {
          "entity": "mcp-operation",
          "effect": "changes",
          "from": "Pending approval",
          "to": "Running",
          "facts": []
        }
      ]
    },
    {
      "text": "Record SMTP acceptance despite later Sent-copy failure.",
      "kind": "product",
      "actor": "mcp-client",
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      },
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
      ]
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/compose.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/quickReplySend.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/pendingSends.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Compose.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+QuickReply.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/sidecar/dispatch/compose.rs"
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


# Send message — sent copy or cleanup mcp

## Trigger

SMTP acceptance succeeds but later Sent append/cache or consumed-copy cleanup fails.

## Outcome

Acceptance remains the send outcome; later failure does not prove non-delivery.
