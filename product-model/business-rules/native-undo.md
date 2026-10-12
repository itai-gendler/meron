---
{
  "appliesTo": [
    {
      "type": "capability",
      "id": "undo-mail-move"
    },
    {
      "type": "capability",
      "id": "move-message"
    },
    {
      "type": "capability",
      "id": "archive-message"
    },
    {
      "type": "capability",
      "id": "trash-message"
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/mailMoves.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+ThreadMoves.kt"
    }
  ]
}
---


# Undo follows the identifiers retained by its native caller

Desktop reverses supported moves using returned destination identifiers. Mobile resolves a thread and does not establish exact original-selection-only rollback. Missing history or reverse errors do not prove restored state.
