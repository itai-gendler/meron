---
{
  "entities": [
    {
      "entity": "mail-account",
      "shows": [
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
      ],
      "collects": [
        "Display name",
        "Sender name",
        "Connection configuration",
        "Certificate trust",
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
    },
    {
      "entity": "account-alias",
      "shows": [
        "Address",
        "Display name"
      ],
      "collects": [
        "Address",
        "Display name"
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


# Mail account

Read and edit the selected mail account and configured aliases.
