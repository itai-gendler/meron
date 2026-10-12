---
{
  "kind": "alternative",
  "routes": {
    "mcp": "Mcp"
  },
  "steps": [
    {
      "text": "Request read conversation.",
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
      "text": "Subscription-backed content is selected.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      }
    },
    {
      "text": "Available cached contents, dates, links and flags are presented instead of SMTP/IMAP mail.",
      "kind": "product",
      "entities": [
        {
          "entity": "feed",
          "effect": "reads",
          "facts": [
            "URL",
            "Title",
            "Synchronization information",
            "Error"
          ]
        },
        {
          "entity": "feed-item",
          "effect": "reads",
          "facts": [
            "Title",
            "Author",
            "Link",
            "Published date",
            "Updated date",
            "Fetched date",
            "Content",
            "Media",
            "Unread",
            "Starred"
          ]
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

# Read conversation — feed mcp

## Trigger

Subscription-backed content is selected.

## Outcome

Available cached contents, dates, links and flags are presented instead of SMTP/IMAP mail.
