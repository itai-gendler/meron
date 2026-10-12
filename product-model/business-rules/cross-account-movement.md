---
{
  "appliesTo": [
    {
      "type": "capability",
      "id": "move-message"
    },
    {
      "type": "capability",
      "id": "copy-message"
    },
    {
      "type": "capability",
      "id": "undo-mail-move"
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
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+ThreadMoves.kt#copyThreadToFolder"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+ThreadMoves.kt"
    }
  ]
}
---



# Cross-account movement preserves copy-before-delete and mobile target limits

Desktop movement copies to the destination before source removal; a later removal failure leaves both. Mobile other-account column choices omit the destination-account argument, resolving the source account and allowing a source-account move, no-op or failure instead of established selected-other-account success.

The inspected mobile copy-to-folder caller does supply the chosen destination account. Its cross-account copy leaves the source intact; the omitted-account limitation applies to mobile movement to another-account Kanban columns.
