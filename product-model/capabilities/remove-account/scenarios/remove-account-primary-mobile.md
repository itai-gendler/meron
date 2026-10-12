---
{
  "kind": "primary",
  "routes": {
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request remove account.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::mailbox"
        },
        "ios": {
          "place": "ios::mailbox"
        }
      }
    },
    {
      "text": "The selected configured connection profile is confirmed for local removal and core cleanup succeeds.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::mailbox"
        },
        "ios": {
          "place": "ios::mailbox"
        }
      }
    },
    {
      "text": "Forget the local account, its configured aliases, folders and cached mail representations; attempt its secret/media cleanup. The remote mailbox and remote messages remain unchanged, and retained local to-do mail references can become stale.",
      "kind": "product",
      "entities": [
        {
          "entity": "mail-account",
          "effect": "removes"
        },
        {
          "entity": "folder",
          "effect": "removes",
          "with": "mail-account"
        },
        {
          "entity": "email-message",
          "effect": "removes",
          "with": "folder"
        },
        {
          "entity": "account-alias",
          "effect": "removes",
          "with": "mail-account"
        }
      ],
      "contexts": {
        "android": {
          "place": "android::mailbox"
        },
        "ios": {
          "place": "ios::mailbox"
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp.go#removeAccount"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/accounts.go#accountRemove"
    }
  ]
}
---


# Remove account — primary

## Trigger

The selected configured mail account is confirmed for local removal and core cleanup succeeds.

## Outcome

The local mail account and its cached/configured contents are removed. Remote mailbox contents remain, and retained Task mail references can become stale.

## Decision points

### Local caller

Which native caller performs the removal?

- Desktop → Prune explicit MCP account selections before the core removal; core failures can be logged/suppressed.
- Android or iOS → Use the mobile core removal result before updating selected native state.
