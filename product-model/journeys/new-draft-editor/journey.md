---
{
  "actors": [
    "user"
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

# Edit the composition opened by creation

## Goal

Edit the composition opened by creation.

## Success criterion

The Product opens the supported full editor with the prepared composition and the person edits it.
