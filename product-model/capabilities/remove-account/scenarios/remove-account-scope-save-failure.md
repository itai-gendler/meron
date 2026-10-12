---
{
  "kind": "edge",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request removal of the selected account.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        }
      }
    },
    {
      "text": "Desktop must prune a configured explicit client selection, but saving that configuration fails.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        }
      }
    },
    {
      "text": "Return the scope-save error before invoking local account cleanup.",
      "kind": "product",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/accounts.go#accountRemove"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp.go#removeAccount"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp.go#save"
    }
  ]
}
---

# Remove account — scope save failure

## Trigger

An explicit MCP selection contains the account, and persistence of its removal fails.

## Outcome

Desktop returns the pruning error before calling core account removal. The old client configuration and local account data remain; this refusal is distinct from the later suppressed core-removal error.
