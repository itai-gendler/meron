---
{
  "appliesTo": [
    {
      "type": "capability",
      "id": "send-message"
    },
    {
      "type": "capability",
      "id": "retry-send"
    },
    {
      "type": "capability",
      "id": "save-draft"
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

# SMTP acceptance does not imply recipient delivery or complete cleanup

SMTP acceptance is the send success boundary. Sent append/cache and consumed-draft cleanup can fail or complete later. Transport failure can leave delivery uncertain. Core Sent-copy errors after acceptance do not become a failed send; retry contents/idempotency are not unlimited or restart-safe.
