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
      "id": "save-draft"
    },
    {
      "type": "capability",
      "id": "discard-draft"
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+QuickReply.kt#dispatchQuickReplySend"
    }
  ]
}
---


# Draft replacement and consumption use stable message identity

Stored Draft copies use stable identity for replacement/cleanup. MCP replacement is a supported whole-content replacement in Drafts. Save/autosave coordinate with send/discard so consumed content is not resurrected; partial remote cleanup can leave copies.

Native generation/ownership checks preserve a newer reply that still uses the same saved identity while an earlier send settles. Only copies consumed by that settled send and no longer in use are eligible for its cleanup.
