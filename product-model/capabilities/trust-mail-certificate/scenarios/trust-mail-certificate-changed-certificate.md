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
      "text": "The endpoint/protocol presents a different fingerprint.",
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
      "text": "The new certificate is not implicitly trusted and connection remains blocked pending explicit acceptance.",
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
    }
  ]
}
---

# Trust mail certificate — changed certificate

## Trigger

The endpoint/protocol presents a different fingerprint.

## Outcome

The new certificate is not implicitly trusted and connection remains blocked pending explicit acceptance.
