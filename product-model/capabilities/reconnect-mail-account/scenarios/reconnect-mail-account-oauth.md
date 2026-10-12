---
{
  "kind": "alternative",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request reconnect connection profile.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::account-setup"
        }
      }
    },
    {
      "text": "Return the provider result to the pending redirect URI.",
      "kind": "actor",
      "actor": "identity-provider",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "oauth-callback"
        }
      }
    },
    {
      "text": "Validate redirect, pending state, provider error, authorization code and verifier before token exchange.",
      "kind": "product",
      "actor": "identity-provider",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "oauth-callback"
        }
      }
    },
    {
      "text": "The pending OAuth flow receives matching state, the expected redirect and a nonempty code.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::account-setup"
        }
      }
    },
    {
      "text": "After successful token/profile exchange, connection credentials are retained; a desktop callback success page alone does not prove token exchange or persistence.",
      "kind": "product",
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
      "target": "desktop/oauth.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/shared/src/commonMain/kotlin/jp/nonbili/meron/shared/OAuthFlow.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+OAuth.kt"
    }
  ]
}
---


# Reconnect mail account — oauth

## Trigger

The pending OAuth flow receives matching state, the expected redirect and a nonempty code.

## Outcome

After successful token/profile exchange, connection credentials are retained; a desktop callback success page alone does not prove token exchange or persistence.
