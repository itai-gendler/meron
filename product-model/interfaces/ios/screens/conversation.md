---
{
  "entities": [
    {
      "entity": "email-message",
      "shows": [
        "Location",
        "Message identity",
        "Sender",
        "Recipients",
        "Reply information",
        "Subject",
        "Date",
        "Plain content",
        "HTML content",
        "Thread information",
        "Unread",
        "Starred",
        "Body availability"
      ]
    },
    {
      "entity": "draft",
      "shows": [
        "Save status"
      ],
      "collects": [
        "Sending identity",
        "Recipients",
        "Subject",
        "Plain content"
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
      "entity": "attachment",
      "shows": [
        "Filename",
        "Media type",
        "Size",
        "Content availability"
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



# Conversation

Read a selected grouped conversation as chat or traditional mail and prepare a quick reply.
