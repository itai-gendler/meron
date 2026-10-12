---
{
  "kind": "alternative",
  "routes": {
    "desktop": "Desktop",
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request import subscription.",
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
      "text": "OPML includes an already subscribed URL.",
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
      "text": "Existing URLs are skipped while valid new subscriptions can be retained.",
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
    }
  ]
}
---

# Import feeds — duplicates skipped

## Trigger

OPML includes an already subscribed URL.

## Outcome

Existing URLs are skipped while valid new subscriptions can be retained.
