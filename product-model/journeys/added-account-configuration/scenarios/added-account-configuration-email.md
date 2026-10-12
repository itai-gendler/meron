---
{
  "kind": "primary",
  "result": "achieved",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Submit the supported account connection input.",
      "kind": "actor",
      "actor": "user",
      "capability": "add-mail-account",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::account-setup"
        }
      }
    },
    {
      "text": "Persist the successfully connected mail account through this native setup handler.",
      "kind": "product",
      "actor": "user",
      "capability": "add-mail-account",
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
        }
      }
    },
    {
      "text": "Select the newly created account in its account settings panel.",
      "kind": "product",
      "actor": "user",
      "capability": "add-mail-account",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mail-account"
        }
      }
    },
    {
      "text": "Choose a supported account preference and save it.",
      "kind": "actor",
      "actor": "user",
      "capability": "change-mail-account-settings",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mail-account"
        }
      }
    },
    {
      "text": "Retain the chosen mail account preference in the selected account.",
      "kind": "product",
      "actor": "user",
      "capability": "change-mail-account-settings",
      "entities": [
        {
          "entity": "mail-account",
          "effect": "changes",
          "facts": [
            "Display name",
            "Sender name",
            "Signature",
            "Load remote images",
            "Conversation HTML",
            "Unified inclusion",
            "Muted",
            "Paused",
            "Save sent copy",
            "Avatar",
            "Wallpaper"
          ]
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::mail-account"
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


# Configure the account just created in Settings — email

## Trigger

The person adds an account from desktop Settings and setup succeeds.

## Outcome

The newly created account is selected in its settings panel and its supported preferences are changed.
