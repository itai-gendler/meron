---
{
  "kind": "validation",
  "routes": {
    "android": "Android"
  },
  "steps": [
    {
      "text": "Request open attached file.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::message"
        }
      }
    },
    {
      "text": "Android selects a prohibited file type for opening.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::message"
        }
      }
    },
    {
      "text": "The host refuses unsafe file opening.",
      "kind": "product",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::message"
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

# Open attachment — blocked file

## Trigger

Android selects a prohibited file type for opening.

## Outcome

The host refuses unsafe file opening.
