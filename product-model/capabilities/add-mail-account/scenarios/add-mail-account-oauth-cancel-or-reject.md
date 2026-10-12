---
{
  "kind": "edge",
  "routes": {
    "desktop": "Desktop",
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request add connection profile.",
      "kind": "actor",
      "actor": "user",
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
      "text": "Return the provider result to the pending redirect URI.",
      "kind": "actor",
      "actor": "identity-provider",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "oauth-callback"
        },
        "android": {
          "place": "oauth-callback"
        },
        "ios": {
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
        },
        "android": {
          "place": "oauth-callback"
        },
        "ios": {
          "place": "oauth-callback"
        }
      }
    },
    {
      "text": "The callback is cancelled, has a provider error, mismatches state/redirect, lacks a code, or token/profile exchange fails.",
      "kind": "condition",
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
      "text": "No successful connected account is established from the rejected or failed flow.",
      "kind": "product",
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


# Add mail account — oauth cancel or reject

## Trigger

The callback is cancelled, has a provider error, mismatches state/redirect, lacks a code, or token/profile exchange fails.

## Outcome

No successful connected account is established from the rejected or failed flow.
