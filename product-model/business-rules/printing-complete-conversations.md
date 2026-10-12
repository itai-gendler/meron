---
{
  "appliesTo": [
    {
      "type": "capability",
      "id": "print-message"
    },
    {
      "type": "capability",
      "id": "print-conversation"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/lib/printMail.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/PrintMail.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/iosMain/kotlin/jp/nonbili/meron/ui/PrintMail.ios.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/androidMain/kotlin/jp/nonbili/meron/ui/PrintMail.android.kt"
    }
  ]
}
---

# Conversation printing loads the full supported conversation without read marking

Conversation print loads full pages, preserves order, deduplicates and detects non-progress/broken paging; a print failure does not claim exhaustive physical output. iOS prepares plain content. Printing does not set Unread.
