---
{
  "relations": [
    {
      "entity": "folder",
      "verb": "has",
      "cardinality": "one-to-many"
    },
    {
      "entity": "account-alias",
      "verb": "has",
      "cardinality": "one-to-many"
    },
    {
      "entity": "draft",
      "verb": "has",
      "cardinality": "one-to-many"
    },
    {
      "entity": "outgoing-send",
      "verb": "has",
      "cardinality": "one-to-many"
    },
    {
      "entity": "kanban-column",
      "verb": "supplies",
      "cardinality": "one-to-many"
    },
    {
      "entity": "mcp-operation",
      "verb": "is targeted by",
      "cardinality": "one-to-many"
    }
  ],
  "domain": "mail-accounts",
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

Added/upserted, reconnected, configured, synchronized and locally removed.

## Information kept

- **Address** — The configured email address, normalized where the operation requires it.
- **Display name** — The human-facing label retained for this entry.
- **Sender name** — The default display name used for the sending identity.
- **Provider** — The configured password or OAuth provider.
- **Connection configuration** — IMAP/SMTP hosts, ports, security modes, username, authentication method and account proxy selection.
- **Credentials** — Opaque password or OAuth material retained through the supported secret store.
- **Credential availability** — Whether the configured secret can currently be obtained.
- **Needs reconnect** — The inspected indication that connection credentials require user repair.
- **Certificate trust** — Accepted endpoint/protocol certificate fingerprints.
- **Signature** — Retained signature HTML and account follow/custom/none choice where applicable.
- **Load remote images** — Whether this account loads remote images without per-message reveal.
- **Conversation HTML** — Whether this account presents HTML content in conversations.
- **Unified inclusion** — Whether this account participates in native unified results.
- **Muted** — Whether notifications for this account are muted.
- **Paused** — Whether automatic checking for this account is paused.
- **Save sent copy** — Whether Sent-copy saving is enabled, disabled or follows the provider default.
- **Order** — The retained order among sibling entries.
- **Avatar** — The configured image/reference for this account.
- **Wallpaper** — The configured reading wallpaper choices and image references.
