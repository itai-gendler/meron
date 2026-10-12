---
{
  "kind": "edge",
  "routes": {
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request change message settings.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::messages-settings"
        },
        "ios": {
          "place": "ios::messages-settings"
        }
      }
    },
    {
      "text": "A supported Messages preference write fails.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::messages-settings"
        },
        "ios": {
          "place": "ios::messages-settings"
        }
      }
    },
    {
      "text": "The applicable caller reports failure or retains the preceding message-presentation preferences. The failed choice is not established as saved.",
      "kind": "product",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::messages-settings"
        },
        "ios": {
          "place": "ios::messages-settings"
        }
      },
      "actor": "user"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/settings.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/components/dialog/SettingsDialog.tsx"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/SettingsUi.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/shared/src/commonMain/kotlin/jp/nonbili/meron/shared/RemoteContent.kt"
    }
  ]
}
---


# Change message settings — write failure mobile

## Trigger

A supported Messages preference write fails.

## Outcome

The applicable caller reports failure or retains the preceding message-presentation preferences. The failed choice is not established as saved.
