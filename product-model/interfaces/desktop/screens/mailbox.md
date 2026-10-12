---
{
  "entities": [
    {
      "entity": "mail-account",
      "shows": [
        "Address",
        "Display name",
        "Provider",
        "Order",
        "Muted",
        "Paused"
      ]
    },
    {
      "entity": "feed-account",
      "shows": [
        "Display name",
        "Order",
        "Muted",
        "Paused"
      ]
    },
    {
      "entity": "folder",
      "shows": [
        "Name",
        "Hierarchy",
        "Role",
        "Unread count"
      ]
    },
    {
      "entity": "email-message",
      "shows": [
        "Location",
        "Sender",
        "Recipients",
        "Subject",
        "Date",
        "Unread",
        "Starred",
        "Body availability"
      ]
    },
    {
      "entity": "feed-item",
      "shows": [
        "Title",
        "Author",
        "Published date",
        "Unread",
        "Starred"
      ]
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


# Mailbox

Browse the selected mailbox or merged account scope, search/filter/page results and choose source folders.
