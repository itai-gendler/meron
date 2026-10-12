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
      "text": "Request edit configured sending identity.",
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
      "text": "An existing configured sending identity receives a valid replacement address or display name.",
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
      "text": "Replace the selected alias address/name in the selected account list. The complete retained alias list reflects this identity change; MCP writes replace the complete list and do not verify external address ownership.",
      "kind": "product",
      "entities": [
        {
          "entity": "account-alias",
          "effect": "changes",
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

# Edit account alias — primary native

## Trigger

An existing configured sending identity receives a valid replacement address or display name.

## Outcome

Replace the selected alias address/name in the selected account list. The complete retained alias list reflects this identity change; MCP writes replace the complete list and do not verify external address ownership.
