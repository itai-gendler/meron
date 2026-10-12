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
      "text": "A supported RSS-account preference write fails.",
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
      "text": "The caller retains its error or prior RSS preferences; the failed field is not established as saved. Earlier successful fields can remain.",
      "kind": "product",
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


# Change feed account settings — write failure native

## Trigger

A supported RSS-account preference write fails.

## Outcome

The caller retains its error or prior RSS preferences; the failed field is not established as saved. Earlier successful fields can remain.
