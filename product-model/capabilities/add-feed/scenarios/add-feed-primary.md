---
{
  "kind": "primary",
  "routes": {
    "desktop": "Desktop",
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request add subscription.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::feed"
        },
        "android": {
          "place": "android::feed"
        },
        "ios": {
          "place": "ios::feed"
        }
      }
    },
    {
      "text": "A new subscription URL fetches and parses supported subscription content.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::feed"
        },
        "android": {
          "place": "android::feed"
        },
        "ios": {
          "place": "ios::feed"
        }
      }
    },
    {
      "text": "Retain the resolved feed and its initially fetched items together. The fetched titles, contents, dates and initial flags are available under the selected RSS account.",
      "kind": "product",
      "entities": [
        {
          "entity": "feed",
          "effect": "creates",
          "facts": [
            "URL",
            "Title",
            "Synchronization information",
            "Error"
          ]
        },
        {
          "entity": "feed-item",
          "effect": "creates",
          "with": "feed",
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
        "desktop": {
          "place": "desktop::feed"
        },
        "android": {
          "place": "android::feed"
        },
        "ios": {
          "place": "ios::feed"
        }
      },
      "actor": "user"
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/rss.rs#store_parsed_feed"
    }
  ]
}
---


# Add feed — primary

## Trigger

A new subscription URL fetches and parses supported feed content.

## Outcome

Fetch/parse the supplied subscription URL and retain it under the selected feed account. The subscription is available with its obtained title/items; fetching failure does not establish a successful subscription.
