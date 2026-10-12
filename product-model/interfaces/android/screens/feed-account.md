---
{
  "entities": [
    {
      "entity": "feed-account",
      "shows": [
        "Display name",
        "Load remote images",
        "Conversation HTML",
        "Unified inclusion",
        "Muted",
        "Paused",
        "Polling interval",
        "Order",
        "Avatar",
        "Wallpaper"
      ],
      "collects": [
        "Display name",
        "Load remote images",
        "Conversation HTML",
        "Unified inclusion",
        "Muted",
        "Paused",
        "Polling interval",
        "Avatar",
        "Wallpaper"
      ]
    },
    {
      "entity": "feed",
      "shows": [
        "URL",
        "Title",
        "Synchronization information",
        "Error"
      ],
      "collects": [
        "URL"
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


# Feed account

Read and edit the selected feed account and its independently addressed subscriptions.
