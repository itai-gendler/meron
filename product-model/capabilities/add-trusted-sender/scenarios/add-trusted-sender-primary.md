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
      "text": "Request add allowlisted address.",
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
      "text": "A valid normalized sender address is selected for persistent trust and its save succeeds.",
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
      "text": "Normalize and persist the selected sender address in the app-wide remote-content allowlist. The sender has a retained allowlist entry used by subsequent remote-content preparation.",
      "kind": "product",
      "entities": [
        {
          "entity": "trusted-sender",
          "effect": "creates",
          "facts": [
            "Address"
          ]
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

# Add trusted sender — primary

## Trigger

A valid normalized sender address is selected for persistent trust and its save succeeds.

## Outcome

Normalize and persist the selected sender address in the app-wide remote-content allowlist. The sender has a retained allowlist entry used by subsequent remote-content preparation.
