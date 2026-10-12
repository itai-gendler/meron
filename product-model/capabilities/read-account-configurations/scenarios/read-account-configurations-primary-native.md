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
      "text": "Request read account configurations.",
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
      "text": "Retained account configuration is available through the supported settings read.",
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
      "text": "Read the selected native configuration, or the app-wide nonsecret configuration returned by the management tool. The applicable account configuration is available; opaque passwords, OAuth tokens and proxy credentials are not revealed.",
      "kind": "product",
      "entities": [
        {
          "entity": "mail-account",
          "effect": "reads",
          "facts": [
            "Address",
            "Display name",
            "Sender name",
            "Provider",
            "Connection configuration",
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
        },
        {
          "entity": "feed-account",
          "effect": "reads",
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
        },
        {
          "entity": "account-alias",
          "effect": "reads",
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_configuration.go#configurationAccounts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/types.go#Account"
    }
  ]
}
---


# Read account configurations — primary native

## Trigger

Retained account configuration is available through the supported settings read.

## Outcome

Read the selected native configuration, or the app-wide nonsecret configuration returned by the management tool. The applicable account configuration is available; opaque passwords, OAuth tokens and proxy credentials are not revealed.
