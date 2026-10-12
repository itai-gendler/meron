---
{
  "kind": "primary",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request mute account.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        }
      }
    },
    {
      "text": "The selected account is not muted and Mute is chosen.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        }
      }
    },
    {
      "text": "Persist Muted as true for the selected account through the desktop account action. The selected account notification choice is changed; the account contents remain.",
      "kind": "product",
      "entities": [
        {
          "entity": "mail-account",
          "effect": "changes",
          "facts": [
            "Muted"
          ]
        },
        {
          "entity": "feed-account",
          "effect": "changes",
          "facts": [
            "Muted"
          ]
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
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

# Mute account — primary

## Trigger

The selected account is not muted and Mute is chosen.

## Outcome

Persist Muted as true for the selected account through the desktop account action. The selected account notification choice is changed; the account contents remain.
