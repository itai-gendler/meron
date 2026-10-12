---
{
  "appliesTo": [
    {
      "type": "capability",
      "id": "create-draft"
    },
    {
      "type": "capability",
      "id": "edit-draft"
    },
    {
      "type": "capability",
      "id": "send-message"
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

# MCP composition accepts only its bounded plain-text contract

MCP accepts supported To/Cc/Bcc, subject, plain body and reply/reference headers. Header newline/syntax/length and recipient checks apply; body is bounded to 128 KiB and supported header values to 8192 bytes. It supports neither arbitrary sender override nor composition attachments.
