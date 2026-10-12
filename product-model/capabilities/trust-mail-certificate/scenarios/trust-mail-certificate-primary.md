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
      "text": "Request trust mail certificate.",
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
      "text": "The failed attempt has a probed endpoint/protocol fingerprint and the person explicitly accepts that fingerprint.",
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
      "text": "Probe the relevant IMAP/SMTP endpoint, present its fingerprint, retain the user-accepted protocol-specific pin, and retry the supported failed attempt. The accepted trust choice is retained for that endpoint/protocol; another changed or rejected certificate can require a new prompt.",
      "kind": "product",
      "entities": [
        {
          "entity": "mail-account",
          "effect": "changes",
          "facts": [
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
    }
  ]
}
---

# Trust mail certificate — primary

## Trigger

The failed attempt has a probed endpoint/protocol fingerprint and the person explicitly accepts that fingerprint.

## Outcome

Probe the relevant IMAP/SMTP endpoint, present its fingerprint, retain the user-accepted protocol-specific pin, and retry the supported failed attempt. The accepted trust choice is retained for that endpoint/protocol; another changed or rejected certificate can require a new prompt.
