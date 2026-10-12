---
{
  "availability": [
    {
      "place": "desktop"
    },
    {
      "place": "android"
    },
    {
      "place": "ios"
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

# Print conversation

Load every page of the selected conversation, deduplicate and order messages, then prepare them for host printing without read marking. The print request includes the complete obtained conversation, not just the currently loaded reading page.
