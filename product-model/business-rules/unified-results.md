---
{
  "appliesTo": [
    {
      "type": "capability",
      "id": "browse-accounts"
    },
    {
      "type": "capability",
      "id": "browse-messages"
    },
    {
      "type": "capability",
      "id": "refresh-messages"
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

# Merged results retain their actual source scope and bounds

Native Unified merges only included accounts. MCP fan-out uses the acting client’s scope. Search/paging can be incomplete, truncated or partly failed; a merged result is not a universal exhaustive server snapshot.
