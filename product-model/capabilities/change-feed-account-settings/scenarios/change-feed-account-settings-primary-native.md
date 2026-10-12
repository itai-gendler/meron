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
      "text": "Request change subscription grouping settings.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::feed-account"
        },
        "android": {
          "place": "android::feed-account"
        },
        "ios": {
          "place": "ios::feed-account"
        }
      }
    },
    {
      "text": "The selected subscription grouping receives valid preferences meaningful to that source type.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::feed-account"
        },
        "android": {
          "place": "android::feed-account"
        },
        "ios": {
          "place": "ios::feed-account"
        }
      }
    },
    {
      "text": "Persist selected subscription-account preferences; native polling/media choices and the meaningful MCP preference subset remain distinct. The selected subscription-account preference is retained without introducing email transport.",
      "kind": "product",
      "entities": [
        {
          "entity": "feed-account",
          "effect": "changes",
          "facts": [
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
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::feed-account"
        },
        "android": {
          "place": "android::feed-account"
        },
        "ios": {
          "place": "ios::feed-account"
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

# Change feed account settings — primary native

## Trigger

The selected subscription grouping receives valid preferences meaningful to that source type.

## Outcome

Persist selected feed-account preferences; native polling/media choices and the meaningful MCP preference subset remain distinct. The selected feed-account preference is retained without introducing email transport.
