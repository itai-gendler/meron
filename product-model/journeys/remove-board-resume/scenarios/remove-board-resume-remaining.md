---
{
  "kind": "primary",
  "result": "achieved",
  "routes": {
    "desktop": "Desktop",
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Choose Remove for the selected board.",
      "kind": "actor",
      "actor": "user",
      "capability": "remove-board",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::kanban-board"
        },
        "android": {
          "place": "android::kanban-board"
        },
        "ios": {
          "place": "ios::kanban-board"
        }
      }
    },
    {
      "text": "Remove the kanban board and its columns while retaining all backing content.",
      "kind": "product",
      "actor": "user",
      "capability": "remove-board",
      "entities": [
        {
          "entity": "kanban-board",
          "effect": "removes",
          "as": "removed-board"
        },
        {
          "entity": "kanban-column",
          "effect": "removes",
          "with": "removed-board",
          "as": "removed-columns"
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::kanban-board"
        },
        "android": {
          "place": "android::kanban-board"
        },
        "ios": {
          "place": "ios::kanban-board"
        }
      }
    },
    {
      "text": "Select the remaining board and load its source columns.",
      "kind": "product",
      "actor": "user",
      "capability": "remove-board",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::kanban-board"
        },
        "android": {
          "place": "android::kanban-board"
        },
        "ios": {
          "place": "ios::kanban-board"
        }
      }
    },
    {
      "text": "Read the selected board contents.",
      "kind": "actor",
      "actor": "user",
      "capability": "browse-board",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::kanban-board"
        },
        "android": {
          "place": "android::kanban-board"
        },
        "ios": {
          "place": "ios::kanban-board"
        }
      }
    },
    {
      "text": "Read the remaining kanban board and its columns with their available backing mail and feed item summaries.",
      "kind": "product",
      "actor": "user",
      "capability": "browse-board",
      "entities": [
        {
          "entity": "kanban-board",
          "effect": "reads",
          "facts": [
            "Name",
            "Avatar",
            "Wallpaper",
            "Order"
          ],
          "as": "remaining-board"
        },
        {
          "entity": "kanban-column",
          "effect": "reads",
          "facts": [
            "Source account",
            "Folder selection",
            "Filter",
            "Attachments only",
            "Order"
          ],
          "as": "remaining-columns"
        },
        {
          "entity": "email-message",
          "effect": "reads",
          "facts": [
            "Location",
            "Sender",
            "Subject",
            "Date",
            "Unread",
            "Starred",
            "Body availability"
          ]
        },
        {
          "entity": "feed-item",
          "effect": "reads",
          "facts": [
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
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::kanban-board"
        },
        "android": {
          "place": "android::kanban-board"
        },
        "ios": {
          "place": "ios::kanban-board"
        }
      }
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
    },
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



# Continue after removing the selected board — remaining

## Trigger

Removal of the selected board succeeds and another board remains to select.

## Outcome

The Product selects a remaining board or the desktop Mail fallback and that source is read.
