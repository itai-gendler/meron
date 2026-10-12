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
      "text": "Request open attached file.",
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
      "text": "The attached file is not an image preview.",
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
      "text": "The applicable host file association or sharing route handles the handoff.",
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

# Open attachment — non image

## Trigger

The attached file is not an image preview.

## Outcome

The applicable host file association or sharing route handles the handoff.
