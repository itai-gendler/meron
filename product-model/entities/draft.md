---
{
  "relations": [
    {
      "entity": "attachment",
      "verb": "has",
      "cardinality": "one-to-many"
    },
    {
      "entity": "email-message",
      "verb": "has stored copies",
      "cardinality": "one-to-many"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/compose.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/quickReplySend.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/pendingSends.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Compose.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+QuickReply.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/sidecar/dispatch/compose.rs"
    }
  ]
}
---

# Draft

Related attachments are separate. States Editing, Saved. Native editing/saving and MCP stored replacement remain distinct cases. Discard or consumed-draft cleanup removes applicable copies/buffers.

## Information kept

- **Sending identity** — The selected primary account or configured alias for native sending.
- **Recipients** — To, Cc and supported recipient header information.
- **Subject** — The retained subject text.
- **Plain content** — The retained plain-text message body.
- **HTML content** — The retained HTML body, subject to display preparation.
- **Reply information** — Reply-To, In-Reply-To, References and derived reply recipients as applicable.
- **Message identity** — The message identity used for draft replacement, threading or copy reconciliation.
- **Stored copies** — The server Drafts copies matched through the stable draft message identity.
- **Save status** — The observable draft save/in-flight/failure information.

## States

### Editing

An editable native composition buffer.

### Saved

A draft retained in the account Drafts folder.
