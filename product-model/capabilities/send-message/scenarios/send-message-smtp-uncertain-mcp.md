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
      "text": "Transport fails without proving whether the server accepted the contents.",
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
      "text": "Record the uncertain transport failure.",
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
          "to": "Failed",
          "facts": [
            "Result",
            "Error",
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


# Send message — smtp uncertain mcp

## Trigger

Transport fails without proving whether the server accepted the contents.

## Outcome

The retained operation becomes Failed, records its result/error and clears its executable preview. The transport outcome can remain uncertain. Reusing the same retained request identity returns that operation rather than sending again; a new request does not establish non-delivery of the earlier attempt.
