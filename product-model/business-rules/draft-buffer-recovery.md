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
      "id": "retry-send"
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

# Recovered composition buffers are bounded and are not a durable outbox

Native text-buffer recovery follows the implemented limits. Desktop recovery does not persist attachment contents across restart. Optimistic sends/retry contents are UI/process state, not a durable unbounded outbox. Mobile composition does not establish desktop rich-editor parity.
