---
{
  "relations": [
    {
      "entity": "attachment",
      "verb": "has",
      "cardinality": "one-to-many"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mail.go#threadRead"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/mail.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/mailFlags.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/thread_read.rs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Mail.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Thread.kt"
    }
  ]
}
---


# Email message

Each mailbox copy is addressable; copies are received/cached, flagged, copied, moved, trashed or removed.

## Information kept

- **Location** — The account/folder location and addressable stored copy.
- **Message identity** — The message header identity retained across mailbox copies.
- **Sender** — The sender header information.
- **Recipients** — To, Cc and supported recipient header information.
- **Reply information** — Reply-To, In-Reply-To, References and derived reply recipients as applicable.
- **Subject** — The retained subject text.
- **Date** — The message timestamp presented while reading.
- **Plain content** — The retained plain-text message body.
- **HTML content** — The retained HTML body, subject to display preparation.
- **Thread information** — The account-aware grouping and header information from which conversations are derived.
- **Unread** — Whether this mailbox copy is unread.
- **Starred** — Whether this mailbox copy is starred.
- **Body availability** — Whether usable body content has been obtained or is still missing/loading.
