---
{
  "kind": "edge",
  "routes": {
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request export backup.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::backup"
        },
        "ios": {
          "place": "ios::backup"
        }
      }
    },
    {
      "text": "Preparation, persistence or host publication is cancelled or fails.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::backup"
        },
        "ios": {
          "place": "ios::backup"
        }
      }
    },
    {
      "text": "The requested output is not successfully published; preceding work is not assumed rolled back.",
      "kind": "product",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::backup"
        },
        "ios": {
          "place": "ios::backup"
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/backup.rs#collect"
    }
  ]
}
---


# Export backup — cancelled or failed mobile

## Trigger

Preparation, persistence or host publication is cancelled or fails.

## Outcome

The requested output is not successfully published; preceding work is not assumed rolled back.
