---
{
  "kind": "alternative",
  "routes": {
    "desktop": "Desktop",
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request reconnect connection profile.",
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
      "text": "Replacement server configuration omits a password.",
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
      "text": "The stored password is reused instead of being cleared.",
      "kind": "product",
      "entities": [
        {
          "entity": "mail-account",
          "effect": "changes",
          "facts": [
            "Connection configuration",
            "Credential availability",
            "Needs reconnect"
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


# Reconnect mail account — password preserved

## Trigger

Replacement server configuration omits a password.

## Outcome

The stored password is reused instead of being cleared.
