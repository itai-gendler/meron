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
      "text": "Request change connection profile settings.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mail-account"
        },
        "android": {
          "place": "android::mail-account"
        },
        "ios": {
          "place": "ios::mail-account"
        }
      }
    },
    {
      "text": "The selected mail connection receives valid supported preference values.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mail-account"
        },
        "android": {
          "place": "android::mail-account"
        },
        "ios": {
          "place": "ios::mail-account"
        }
      }
    },
    {
      "text": "Persist the selected mail-account preferences; MCP updates only its supported field and does not replace connection credentials. The supported selected preference is retained; account-specific settings apply to the selected account.",
      "kind": "product",
      "entities": [
        {
          "entity": "mail-account",
          "effect": "changes",
          "facts": [
            "Display name",
            "Sender name",
            "Signature",
            "Load remote images",
            "Conversation HTML",
            "Unified inclusion",
            "Muted",
            "Paused",
            "Save sent copy",
            "Avatar",
            "Wallpaper"
          ]
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::mail-account"
        },
        "android": {
          "place": "android::mail-account"
        },
        "ios": {
          "place": "ios::mail-account"
        }
      },
      "actor": "user"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/accounts.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/components/dialog/useAccountDialog.ts#useAccountDialog"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Accounts.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/protocol/accounts.rs#add_mobile_password_account"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/store/accounts.rs"
    }
  ]
}
---

# Change mail account settings — primary native

## Trigger

The selected mail connection receives valid supported preference values.

## Outcome

Persist the selected mail-account preferences; MCP updates only its supported field and does not replace connection credentials. The supported selected preference is retained; account-specific settings apply to the selected account.
