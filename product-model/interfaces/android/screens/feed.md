---
{
  "entities": [
    {
      "entity": "feed",
      "shows": [
        "URL",
        "Title",
        "Synchronization information",
        "Error"
      ]
    },
    {
      "entity": "feed-item",
      "shows": [
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

Read the selected subscription and its item history.
