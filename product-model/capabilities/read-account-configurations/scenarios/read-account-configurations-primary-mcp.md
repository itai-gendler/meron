---
{
  "kind": "primary",
  "routes": {
    "mcp": "Mcp"
  },
  "steps": [
    {
      "text": "Request read account configurations.",
      "kind": "actor",
      "actor": "mcp-client",
      "entities": [],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      }
    },
    {
      "text": "Retained account configuration is available through the supported settings read.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      }
    },
    {
      "text": "Return all configured accounts and their configured sending aliases, with supported nonsecret connection and preference information and redacted credentials/proxy secrets.",
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
        "mcp": {
          "place": "mcp"
        }
      },
      "actor": "mcp-client"
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
      "target": "desktop/mcp_tools.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_configuration.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_mutations.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_operations.go"
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


# Read account configurations — primary mcp

## Trigger

Retained account configuration is available through the supported settings read.

## Outcome

Read the selected native configuration, or the app-wide nonsecret configuration returned by the management tool. The applicable account configuration is available; opaque passwords, OAuth tokens and proxy credentials are not revealed.
