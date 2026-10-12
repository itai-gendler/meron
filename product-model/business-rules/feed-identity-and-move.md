---
{
  "appliesTo": [
    {
      "type": "capability",
      "id": "add-feed"
    },
    {
      "type": "capability",
      "id": "remove-feed"
    },
    {
      "type": "capability",
      "id": "move-feed"
    },
    {
      "type": "capability",
      "id": "import-feeds"
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

# Subscription URL identity preserves existing contents on reassignment

URL identity controls duplicate subscription handling. Moving to another subscription account reassigns the retained source with its items/read/star flags; a non-RSS target is refused. Removal deletes its local cached items, not the remote site.
