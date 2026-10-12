---
{
  "kind": "validation",
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
      "text": "Native selects a role outside Trash/Junk or MCP selects a role outside Trash.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      }
    },
    {
      "text": "Emptying is refused without permanently removing arbitrary mailbox contents.",
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

# Empty folder — ineligible folder mcp

## Trigger

Native selects a role outside Trash/Junk or MCP selects a role outside Trash.

## Outcome

Emptying is refused without permanently removing arbitrary mailbox contents.
