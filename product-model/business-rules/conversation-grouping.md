---
{
  "appliesTo": [
    {
      "type": "capability",
      "id": "browse-messages"
    },
    {
      "type": "capability",
      "id": "read-conversation"
    },
    {
      "type": "capability",
      "id": "read-message"
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

# Conversations derive from account-aware message grouping

Thread information and cached/server lookups derive conversations. Account identity, copies and subject branches affect grouping. Conversation and Kanban card are projections, not separately persisted workflow records.
