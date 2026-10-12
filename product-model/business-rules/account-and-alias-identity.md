---
{
  "appliesTo": [
    {
      "type": "capability",
      "id": "add-mail-account"
    },
    {
      "type": "capability",
      "id": "reconnect-mail-account"
    },
    {
      "type": "capability",
      "id": "add-account-alias"
    },
    {
      "type": "capability",
      "id": "edit-account-alias"
    },
    {
      "type": "capability",
      "id": "remove-account-alias"
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

# Configured addresses are normalized without ownership verification

Address parsing/normalization defines configured identities. Desktop changed-address editing can create another account instead of migrating the old one. A configured sending alias is not proof of external address ownership.
