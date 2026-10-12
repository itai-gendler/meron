---
{
  "kind": "edge",
  "routes": {
    "desktop": "Desktop",
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request add connection profile.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::account-setup"
        },
        "android": {
          "place": "android::account-setup"
        },
        "ios": {
          "place": "ios::account-setup"
        }
      }
    },
    {
      "text": "Configuration persistence succeeds but secret storage fails or has no usable key.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::account-setup"
        },
        "android": {
          "place": "android::account-setup"
        },
        "ios": {
          "place": "ios::account-setup"
        }
      }
    },
    {
      "text": "Configuration can remain with unavailable credentials; universal atomic persistence is not established.",
      "kind": "product",
      "entities": [
        {
          "entity": "mail-account",
          "effect": "creates",
          "facts": [
            "Address",
            "Display name",
            "Sender name",
            "Provider",
            "Connection configuration",
            "Credentials",
            "Credential availability",
            "Needs reconnect",
            "Certificate trust",
            "Signature",
            "Load remote images",
            "Conversation HTML",
            "Unified inclusion",
            "Muted",
            "Paused",
            "Save sent copy",
            "Order",
            "Avatar",
            "Wallpaper"
          ]
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::account-setup"
        },
        "android": {
          "place": "android::account-setup"
        },
        "ios": {
          "place": "ios::account-setup"
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

# Add mail account — secret storage failure

## Trigger

Configuration persistence succeeds but secret storage fails or has no usable key.

## Outcome

Configuration can remain with unavailable credentials; universal atomic persistence is not established.
