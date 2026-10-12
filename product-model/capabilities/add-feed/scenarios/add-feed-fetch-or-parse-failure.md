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
      "text": "Initial subscription fetching or parsing fails.",
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
      "text": "The fetch/parse error remains without claiming initialized successful contents.",
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

# Add feed — fetch or parse failure

## Trigger

Initial subscription fetching or parsing fails.

## Outcome

The fetch/parse error remains without claiming initialized successful contents.
