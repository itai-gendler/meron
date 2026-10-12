---
{
  "kind": "edge",
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
      "text": "Preparation, persistence or host publication is cancelled or fails.",
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
      "text": "The requested output is not successfully published; preceding work is not assumed rolled back.",
      "kind": "product",
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

# Export feeds — cancelled or failed

## Trigger

Preparation, persistence or host publication is cancelled or fails.

## Outcome

The requested output is not successfully published; preceding work is not assumed rolled back.
