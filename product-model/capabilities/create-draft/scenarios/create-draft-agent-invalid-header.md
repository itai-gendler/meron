---
{
  "kind": "validation",
  "routes": {
    "mcp": "Mcp"
  },
  "steps": [
    {
      "text": "Request create composition.",
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
      "text": "Recipients/headers have invalid syntax, forbidden newlines or excessive lengths.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      }
    },
    {
      "text": "Validation fails before successful stored composition creation.",
      "kind": "product",
      "entities": [],
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

# Create draft — agent invalid header

## Trigger

Recipients/headers have invalid syntax, forbidden newlines or excessive lengths.

## Outcome

Validation fails before successful stored composition creation.
