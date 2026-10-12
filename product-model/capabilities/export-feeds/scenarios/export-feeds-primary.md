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
      "text": "Request export subscription.",
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
      "text": "Retained subscription URLs are available and the host OPML publication succeeds.",
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
      "text": "Serialize the selected account subscriptions as OPML and hand the result to the supported save/export facility. The OPML subscription representation is exported when host writing succeeds; it is not another persistent Feed Entity.",
      "kind": "product",
      "entities": [
        {
          "entity": "feed",
          "effect": "reads",
          "facts": [
            "URL",
            "Title"
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

# Export feeds — primary

## Trigger

Retained subscription URLs are available and the host OPML publication succeeds.

## Outcome

Serialize the selected account subscriptions as OPML and hand the result to the supported save/export facility. The OPML subscription representation is exported when host writing succeeds; it is not another persistent Feed Entity.
