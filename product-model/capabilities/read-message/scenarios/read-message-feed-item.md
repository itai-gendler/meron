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
      "text": "Request read message.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::message"
        },
        "android": {
          "place": "android::message"
        },
        "ios": {
          "place": "ios::message"
        }
      }
    },
    {
      "text": "One subscription content entry is selected.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::message"
        },
        "android": {
          "place": "android::message"
        },
        "ios": {
          "place": "ios::message"
        }
      }
    },
    {
      "text": "Its available content, title, link, dates and flags are presented.",
      "kind": "product",
      "entities": [
        {
          "entity": "feed",
          "effect": "reads",
          "facts": [
            "URL",
            "Title",
            "Synchronization information",
            "Error"
          ]
        },
        {
          "entity": "feed-item",
          "effect": "reads",
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
          "place": "desktop::message"
        },
        "android": {
          "place": "android::message"
        },
        "ios": {
          "place": "ios::message"
        }
      },
      "actor": "user"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mail.go#threadRead"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/mail.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/mailFlags.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/thread_read.rs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Mail.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Thread.kt"
    }
  ]
}
---

# Read message — feed item

## Trigger

One subscription content entry is selected.

## Outcome

Its available content, title, link, dates and flags are presented.
