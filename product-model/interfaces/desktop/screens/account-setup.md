---
{
  "entities": [
    {
      "entity": "mail-account",
      "collects": [
        "Address",
        "Display name",
        "Sender name",
        "Connection configuration",
        "Credentials",
        "Certificate trust"
      ]
    },
    {
      "entity": "feed-account",
      "collects": [
        "Display name"
      ]
    },
    {
      "entity": "feed",
      "collects": [
        "URL"
      ]
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


# Account setup

Connect an account through the supported password, OAuth or feed-account flow. Wizard and trust stages belong to this connection process.
