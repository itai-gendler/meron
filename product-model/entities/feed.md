---
{
  "relations": [
    {
      "entity": "feed-item",
      "verb": "contains",
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



# Feed

An RSS/Atom subscription with a retained URL, synchronization information and fetched item history.

## Information kept

- **URL** — The subscription URL.
- **Title** — The retained subscription title, initially obtained from the resolved feed.
- **Synchronization information** — The retained last-fetch/synchronization information.
- **Error** — The last synchronization error recorded for this subscription.
