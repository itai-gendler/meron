---
{
  "relations": [
    {
      "entity": "feed",
      "verb": "subscribes to",
      "cardinality": "one-to-many"
    },
    {
      "entity": "kanban-column",
      "verb": "supplies",
      "cardinality": "one-to-many"
    }
  ],
  "domain": "feed-accounts",
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/feeds.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/rss.rs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/rss/opml.rs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Mailbox.kt"
    }
  ]
}
---


# Feed account

Added/configured and removed with local subscriptions/items. No mail credentials or SMTP facts.

## Information kept

- **Display name** — The human-facing label retained for this entry.
- **Load remote images** — Whether this account loads remote images without per-message reveal.
- **Conversation HTML** — Whether this account presents HTML content in conversations.
- **Unified inclusion** — Whether this account participates in native unified results.
- **Muted** — Whether notifications for this account are muted.
- **Paused** — Whether automatic checking for this account is paused.
- **Polling interval** — The retained feed checking interval.
- **Order** — The retained order among sibling entries.
- **Avatar** — The configured image/reference for this RSS account.
- **Wallpaper** — The configured reading wallpaper choices and image references.
