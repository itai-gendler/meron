---
{
  "entities": [
    {
      "entity": "draft",
      "shows": [
        "Sending identity",
        "Recipients",
        "Subject",
        "Plain content",
        "HTML content",
        "Save status"
      ],
      "collects": [
        "Sending identity",
        "Recipients",
        "Subject",
        "Plain content",
        "HTML content"
      ]
    },
    {
      "entity": "attachment",
      "shows": [
        "Filename",
        "Media type",
        "Size",
        "Content availability"
      ],
      "collects": [
        "Filename",
        "Media type"
      ]
    },
    {
      "entity": "outgoing-send",
      "shows": [
        "Captured contents",
        "Attempt status",
        "Failure"
      ]
    },
    {
      "entity": "mail-account",
      "shows": [
        "Address",
        "Display name",
        "Sender name"
      ]
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
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/ComposeUi.kt"
    }
  ]
}
---



# Composer

Edit the selected composition and observe its save or sending outcome.
