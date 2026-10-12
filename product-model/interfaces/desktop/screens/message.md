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
      "entity": "feed-item",
      "shows": [
        "Title",
        "Author",
        "Link",
        "Published date",
        "Updated date",
        "Fetched date",
        "Content",
        "Media",
        "Unread",
        "Starred"
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


# Message

Read the selected individual message or feed item and its available media.
