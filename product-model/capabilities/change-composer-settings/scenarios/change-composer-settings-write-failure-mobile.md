---
{
  "kind": "edge",
  "routes": {
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request change composer settings.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::composer-settings"
        },
        "ios": {
          "place": "ios::composer-settings"
        }
      }
    },
    {
      "text": "A supported signature or Composer preference write fails.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::composer-settings"
        },
        "ios": {
          "place": "ios::composer-settings"
        }
      }
    },
    {
      "text": "The applicable caller reports failure or retains preceding composition settings. The failed signature/preference is not established as saved.",
      "kind": "product",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::composer-settings"
        },
        "ios": {
          "place": "ios::composer-settings"
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


# Change composer settings — write failure mobile

## Trigger

A supported signature or Composer preference write fails.

## Outcome

The applicable caller reports failure or retains preceding composition settings. The failed signature/preference is not established as saved.
