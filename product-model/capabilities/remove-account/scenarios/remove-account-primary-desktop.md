---
{
  "kind": "primary",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request remove account.",
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
      "text": "The selected configured connection profile is confirmed for local removal and core cleanup succeeds.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        }
      }
    },
    {
      "text": "Before local removal, prune this account from every explicit configured client selection that contains it.",
      "kind": "product",
      "actor": "user",
      "entities": [
        {
          "entity": "mcp-client",
          "effect": "changes",
          "facts": [
            "Account scope"
          ]
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        }
      }
    },
    {
      "text": "If pruning changed the saved configuration, cancel all pending retained requests and clear their previews.",
      "kind": "product",
      "actor": "user",
      "entities": [
        {
          "entity": "mcp-operation",
          "effect": "changes",
          "from": "Pending approval",
          "to": "Cancelled",
          "facts": [
            "Preview"
          ]
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
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

Prune explicit MCP selections, remove local account configuration/cache/media, and attempt credential cleanup. Successful local removal leaves the remote mailbox intact; retained Task and board references do not acquire an automatic cleanup guarantee.

## Decision points

### Local caller

Which native caller performs the removal?

- Desktop → Prune explicit MCP account selections before the core removal; core failures can be logged/suppressed.
- Android or iOS → Use the mobile core removal result before updating selected native state.

## Edge cases

- Pruning changes only configured explicit selections that contain this account. If none contain it, no client configuration is saved and this step does not cancel pending work. All accounts remains dynamic.
