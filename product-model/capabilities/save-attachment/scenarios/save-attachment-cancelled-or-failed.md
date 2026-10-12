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
      "text": "Request save attached file.",
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
      "text": "Preparation, persistence or host publication is cancelled or fails.",
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
      "text": "The requested output is not successfully published; preceding work is not assumed rolled back.",
      "kind": "product",
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
      },
      "actor": "user"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/paste_image.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Attachments.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/PlatformServices.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/android/src/main/java/jp/nonbili/meron/AndroidUiAdapters.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/iosMain/kotlin/jp/nonbili/meron/ui/IosMainViewController.kt"
    }
  ]
}
---

# Save attachment — cancelled or failed

## Trigger

Preparation, persistence or host publication is cancelled or fails.

## Outcome

The requested output is not successfully published; preceding work is not assumed rolled back.
