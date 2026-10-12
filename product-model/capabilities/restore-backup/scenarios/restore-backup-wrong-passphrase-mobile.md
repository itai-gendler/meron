---
{
  "kind": "validation",
  "routes": {
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request restore backup.",
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
      "text": "Encrypted contents are opened with a wrong passphrase.",
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
      "text": "Decryption fails before applying unreadable contents and a later retry remains possible.",
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
      "target": "meron-core/src/backup.rs#apply"
    }
  ]
}
---


# Restore backup — wrong passphrase mobile

## Trigger

Encrypted contents are opened with a wrong passphrase.

## Outcome

Decryption fails before applying unreadable contents and a later retry remains possible.
