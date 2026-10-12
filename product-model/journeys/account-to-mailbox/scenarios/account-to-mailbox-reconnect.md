---
{
  "kind": "primary",
  "result": "achieved",
  "routes": {
    "desktop": "Desktop",
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Submit the replacement server settings or credentials for the selected connection.",
      "kind": "actor",
      "actor": "user",
      "capability": "reconnect-mail-account",
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
      "text": "Retain the successful replacement connection configuration for the mail account.",
      "kind": "product",
      "actor": "user",
      "capability": "reconnect-mail-account",
      "entities": [
        {
          "entity": "mail-account",
          "effect": "changes",
          "facts": [
            "Connection configuration",
            "Credentials",
            "Credential availability",
            "Needs reconnect",
            "Certificate trust"
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
      }
    },
    {
      "text": "Select the successfully added or reconnected account and open its mailbox.",
      "kind": "product",
      "actor": "user",
      "capability": "reconnect-mail-account",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        },
        "android": {
          "place": "android::mailbox"
        },
        "ios": {
          "place": "ios::mailbox"
        }
      }
    },
    {
      "text": "Read the selected mailbox results.",
      "kind": "actor",
      "actor": "user",
      "capability": "browse-messages",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        },
        "android": {
          "place": "android::mailbox"
        },
        "ios": {
          "place": "ios::mailbox"
        }
      }
    },
    {
      "text": "Return the folder choices and available email summaries for the selected mailbox.",
      "kind": "product",
      "actor": "user",
      "capability": "browse-messages",
      "entities": [
        {
          "entity": "folder",
          "effect": "reads",
          "facts": [
            "Name",
            "Hierarchy",
            "Role",
            "Unread count"
          ]
        },
        {
          "entity": "email-message",
          "effect": "reads",
          "facts": [
            "Location",
            "Sender",
            "Recipients",
            "Subject",
            "Date",
            "Unread",
            "Starred",
            "Body availability"
          ]
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        },
        "android": {
          "place": "android::mailbox"
        },
        "ios": {
          "place": "ios::mailbox"
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
      "target": "desktop/mail.go#threadRead"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/mail.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/mailFlags.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/thread_read.rs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Mail.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Thread.kt"
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


# Use the connected account — reconnect

## Trigger

Reconnection succeeds through a native handler that selects the repaired mailbox.

## Outcome

The newly connected or reconnected account is selected and its mailbox results are read.
