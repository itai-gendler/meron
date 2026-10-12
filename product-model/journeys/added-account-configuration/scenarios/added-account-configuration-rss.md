---
{
  "kind": "primary",
  "result": "achieved",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Submit the RSS account name and optional initial subscription URL.",
      "kind": "actor",
      "actor": "user",
      "capability": "add-feed-account",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::account-setup"
        }
      }
    },
    {
      "text": "Persist the new RSS account with its supported defaults.",
      "kind": "product",
      "actor": "user",
      "capability": "add-feed-account",
      "entities": [
        {
          "entity": "feed-account",
          "effect": "creates",
          "facts": [
            "Display name",
            "Load remote images",
            "Conversation HTML",
            "Unified inclusion",
            "Muted",
            "Paused",
            "Polling interval",
            "Order",
            "Avatar",
            "Wallpaper"
          ]
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::account-setup"
        }
      }
    },
    {
      "text": "Select the newly created account in its account settings panel.",
      "kind": "product",
      "actor": "user",
      "capability": "add-feed-account",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::feed-account"
        }
      }
    },
    {
      "text": "Choose a supported RSS account preference and save it.",
      "kind": "actor",
      "actor": "user",
      "capability": "change-feed-account-settings",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::feed-account"
        }
      }
    },
    {
      "text": "Retain the chosen feed account preference in the selected account.",
      "kind": "product",
      "actor": "user",
      "capability": "change-feed-account-settings",
      "entities": [
        {
          "entity": "feed-account",
          "effect": "changes",
          "facts": [
            "Display name",
            "Load remote images",
            "Conversation HTML",
            "Unified inclusion",
            "Muted",
            "Paused",
            "Polling interval",
            "Avatar",
            "Wallpaper"
          ]
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::feed-account"
        }
      }
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
      "target": "desktop/frontend/src/states/feeds.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/rss.rs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/rss/opml.rs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Mailbox.kt"
    }
  ]
}
---


# Configure the account just created in Settings — rss

## Trigger

The person adds an account from desktop Settings and setup succeeds.

## Outcome

The newly created account is selected in its settings panel and its supported preferences are changed.

## Edge cases

- An initial subscription URL is optional; when supplied it must fetch and parse successfully before the new account and its initial items are committed.
