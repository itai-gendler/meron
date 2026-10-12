---
{
  "relations": [
    {
      "entity": "email-message",
      "verb": "contains",
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


# Folder

Discovered, synchronized, created, configured and deleted. Protected-subtree and notification checks are Rules derived from the actual classification, not fabricated kept eligibility facts.

## Information kept

- **Name** — The synchronized mailbox name used to choose a source or destination.
- **Hierarchy** — The synchronized folder nesting information.
- **Role** — The classified mailbox role used by the supported folder operations.
- **Notification selection** — The optional folder notification choice.
- **Unread count** — The synchronized/updated unread count shown for this folder.
