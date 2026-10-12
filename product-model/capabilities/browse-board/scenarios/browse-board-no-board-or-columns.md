---
{
  "kind": "alternative",
  "routes": {
    "desktop": "Desktop",
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request browse board.",
      "kind": "actor",
      "actor": "user",
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
      "text": "No board exists or the selected board has no columns.",
      "kind": "condition",
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
      "text": "The empty board state remains without fabricated backing mail or workflow stages.",
      "kind": "product",
      "entities": [
        {
          "entity": "kanban-board",
          "effect": "reads",
          "facts": [
            "Name",
            "Avatar",
            "Wallpaper",
            "Order"
          ]
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
          ]
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
      },
      "actor": "user"
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

# Browse board — no board or columns

## Trigger

No board exists or the selected board has no columns.

## Outcome

The empty board state remains without fabricated backing mail or workflow stages.
