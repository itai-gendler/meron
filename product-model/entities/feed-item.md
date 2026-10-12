---
{
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


# Feed item

Fetched, read/flagged and removed with its subscription/account.

## Information kept

- **Title** — The title of this fetched item.
- **Author** — The feed-item author/source attribution.
- **Link** — The item link to its source.
- **Published date** — The item publication time when supplied.
- **Updated date** — The item update time when supplied.
- **Fetched date** — The time the item was obtained.
- **Content** — The retained item contents.
- **Media** — The retained item media references.
- **Unread** — Whether this cached item is unread.
- **Starred** — Whether this cached item is starred.
