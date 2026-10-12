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
      "id": "trust-mail-certificate"
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

# Password connection setup preserves platform validation boundaries

Desktop normally probes IMAP before save; tolerable SMTP certificate-check timeouts do not establish full validation. OAuth bypasses the normal password-mail validation. Mobile can upsert configuration/store credentials before its later check. An omitted replacement password preserves the existing secret. Certificate trust is endpoint/protocol-specific; arbitrary MCP pins and insecure setup are unsupported.
