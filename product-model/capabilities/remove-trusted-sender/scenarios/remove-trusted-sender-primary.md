---
{
  "kind": "primary",
  "routes": {
    "desktop": "Desktop",
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request remove allowlisted address.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::trusted-senders"
        },
        "android": {
          "place": "android::trusted-senders"
        },
        "ios": {
          "place": "ios::trusted-senders"
        }
      }
    },
    {
      "text": "A retained sender address is selected for removal and its save succeeds.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::trusted-senders"
        },
        "android": {
          "place": "android::trusted-senders"
        },
        "ios": {
          "place": "ios::trusted-senders"
        }
      }
    },
    {
      "text": "Remove the selected normalized sender address from the app-wide allowlist. The persistent sender exception is removed; account/current-message choices remain distinct.",
      "kind": "product",
      "entities": [
        {
          "entity": "trusted-sender",
          "effect": "removes"
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::trusted-senders"
        },
        "android": {
          "place": "android::trusted-senders"
        },
        "ios": {
          "place": "ios::trusted-senders"
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

# Remove trusted sender — primary

## Trigger

A retained sender address is selected for removal and its save succeeds.

## Outcome

Remove the selected normalized sender address from the app-wide allowlist. The persistent sender exception is removed; account/current-message choices remain distinct.
