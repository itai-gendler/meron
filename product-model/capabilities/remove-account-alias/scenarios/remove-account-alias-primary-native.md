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
      "text": "Request remove configured sending identity.",
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
      "text": "An existing configured sending identity is selected for removal.",
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
      "text": "Remove the selected alias from the configured account list. The complete retained alias list reflects this identity change; MCP writes replace the complete list and do not verify external address ownership.",
      "kind": "product",
      "entities": [
        {
          "entity": "account-alias",
          "effect": "removes"
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

# Remove account alias — primary native

## Trigger

An existing configured sending identity is selected for removal.

## Outcome

Remove the selected alias from the configured account list. The complete retained alias list reflects this identity change; MCP writes replace the complete list and do not verify external address ownership.
