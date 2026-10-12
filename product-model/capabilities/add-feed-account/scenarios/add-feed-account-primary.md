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
      "text": "Request add subscription grouping.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::account-setup"
        },
        "android": {
          "place": "android::account-setup"
        },
        "ios": {
          "place": "ios::account-setup"
        }
      }
    },
    {
      "text": "A nonblank name is submitted for a new local subscription grouping.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::account-setup"
        },
        "android": {
          "place": "android::account-setup"
        },
        "ios": {
          "place": "ios::account-setup"
        }
      }
    },
    {
      "text": "Save a named local subscription account, retaining the supported account defaults and optional initial subscription input. The new subscription account is selected and can receive subscriptions.",
      "kind": "product",
      "entities": [
        {
          "entity": "feed-account",
          "effect": "creates",
          "facts": [
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
          ]
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::account-setup"
        },
        "android": {
          "place": "android::account-setup"
        },
        "ios": {
          "place": "ios::account-setup"
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

# Add feed account — primary

## Trigger

A nonblank name is submitted for a new local subscription grouping.

## Outcome

Save a named local feed account, retaining the supported account defaults and optional initial subscription input. The new feed account is selected and can receive subscriptions.
