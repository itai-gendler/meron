---
{
  "kind": "alternative",
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
      "text": "A subscription grouping is selected for removal.",
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
      "text": "Its local configuration, subscriptions and cached contents are removed without changing remote sites.",
      "kind": "product",
      "entities": [
        {
          "entity": "feed-account",
          "effect": "removes"
        },
        {
          "entity": "feed",
          "effect": "removes",
          "with": "feed-account"
        },
        {
          "entity": "feed-item",
          "effect": "removes",
          "with": "feed"
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


# Remove account — rss

## Trigger

A subscription grouping is selected for removal.

## Outcome

Its local configuration, subscriptions and cached contents are removed without changing remote sites.

## Edge cases

- Pruning changes only configured explicit selections that contain this account. If none contain it, no client configuration is saved and this step does not cancel pending work. All accounts remains dynamic.
