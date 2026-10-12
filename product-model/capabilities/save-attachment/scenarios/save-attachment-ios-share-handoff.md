---
{
  "kind": "alternative",
  "routes": {
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request save attached file.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "ios": {
          "place": "ios::message"
        }
      }
    },
    {
      "text": "iOS open/save reaches its host adapter.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "ios": {
          "place": "ios::message"
        }
      }
    },
    {
      "text": "The adapter delegates to sharing; separate open/save completion is not established.",
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

# Save attachment — ios share handoff

## Trigger

iOS open/save reaches its host adapter.

## Outcome

The adapter delegates to sharing; separate open/save completion is not established.
