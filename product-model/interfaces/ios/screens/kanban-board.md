---
{
  "entities": [
    {
      "entity": "kanban-board",
      "shows": [
        "Name",
        "Avatar",
        "Wallpaper",
        "Order"
      ],
      "collects": [
        "Name",
        "Avatar",
        "Wallpaper"
      ]
    },
    {
      "entity": "kanban-column",
      "shows": [
        "Source account",
        "Folder selection",
        "Filter",
        "Attachments only",
        "Order"
      ],
      "collects": [
        "Source account",
        "Folder selection",
        "Filter",
        "Attachments only",
        "Order"
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
      "entity": "feed",
      "shows": [
        "URL",
        "Title",
        "Synchronization information",
        "Error"
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
      "target": "desktop/frontend/src/states/kanban.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/lib/kanbanData.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Kanban.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/KanbanUi.kt"
    }
  ]
}
---


# Kanban board

Read and configure the selected source-backed board and its ordered columns.
