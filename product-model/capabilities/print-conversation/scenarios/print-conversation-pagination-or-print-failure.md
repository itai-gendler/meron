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
      "text": "Request print conversation.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::conversation"
        },
        "android": {
          "place": "android::conversation"
        },
        "ios": {
          "place": "ios::conversation"
        }
      }
    },
    {
      "text": "Full paging fails, repeats without progress, or printing fails.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::conversation"
        },
        "android": {
          "place": "android::conversation"
        },
        "ios": {
          "place": "ios::conversation"
        }
      }
    },
    {
      "text": "The failure is reported instead of claiming an exhaustive printed conversation.",
      "kind": "product",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::conversation"
        },
        "android": {
          "place": "android::conversation"
        },
        "ios": {
          "place": "ios::conversation"
        }
      },
      "actor": "user"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/lib/printMail.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/PrintMail.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/iosMain/kotlin/jp/nonbili/meron/ui/PrintMail.ios.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/androidMain/kotlin/jp/nonbili/meron/ui/PrintMail.android.kt"
    }
  ]
}
---

# Print conversation — pagination or print failure

## Trigger

Full paging fails, repeats without progress, or printing fails.

## Outcome

The failure is reported instead of claiming an exhaustive printed conversation.
