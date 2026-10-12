---
{
  "kind": "alternative",
  "routes": {
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request copy image.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::message"
        },
        "ios": {
          "place": "ios::message"
        }
      }
    },
    {
      "text": "The shipped mobile Copy image action is selected.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::message"
        },
        "ios": {
          "place": "ios::message"
        }
      }
    },
    {
      "text": "Platform sharing receives the image rather than promising desktop clipboard copying.",
      "kind": "product",
      "entities": [
        {
          "entity": "attachment",
          "effect": "reads",
          "facts": [
            "Filename",
            "Media type",
            "Size",
            "Content availability",
            "Content location",
            "Inline identity"
          ]
        }
      ],
      "contexts": {
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

# Copy image — mobile share

## Trigger

The shipped mobile Copy image action is selected.

## Outcome

Platform sharing receives the image rather than promising desktop clipboard copying.
