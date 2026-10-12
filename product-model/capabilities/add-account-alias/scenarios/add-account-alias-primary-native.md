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
      "text": "Request add configured sending identity.",
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
      "text": "A valid additional sending address and optional display name are supplied for the selected account.",
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
      "text": "Add the configured address/name to the selected connection profile alias list. The complete retained alias list reflects this identity change; MCP writes replace the complete list and do not verify external address ownership.",
      "kind": "product",
      "entities": [
        {
          "entity": "account-alias",
          "effect": "creates",
          "facts": [
            "Address",
            "Display name"
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

# Add account alias — primary native

## Trigger

A valid additional sending address and optional display name are supplied for the selected account.

## Outcome

Add the configured address/name to the selected mail account alias list. The complete retained alias list reflects this identity change; MCP writes replace the complete list and do not verify external address ownership.
