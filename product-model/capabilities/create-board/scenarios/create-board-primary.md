---
{
  "kind": "primary",
  "routes": {
    "desktop": "Desktop",
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request create board.",
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
      "text": "Native Create is chosen and board persistence succeeds; the name may use its native default.",
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
      "text": "Create the kanban board with its native default name and columns, and select the created subject.",
      "kind": "product",
      "entities": [
        {
          "entity": "kanban-board",
          "effect": "creates",
          "facts": [
            "Name",
            "Avatar",
            "Wallpaper",
            "Order"
          ]
        },
        {
          "entity": "kanban-column",
          "effect": "creates",
          "with": "kanban-board",
          "facts": [
            "Source account",
            "Folder selection",
            "Filter",
            "Attachments only",
            "Order"
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/UiUtils.kt#defaultKanbanBoard"
    }
  ]
}
---


# Create board — primary

## Trigger

Native Create is chosen and board persistence succeeds; the name may use its native default.

## Outcome

Persist a new named board with its supported defaults and select the created board. The newly selected board is ready for reading/configuration; default columns follow the native creation path.

## Decision points

### Initial sources

Which native creation handler supplies the default columns?

- Desktop → the initial column reads Unified Inbox.
- Android or iOS → the initial columns read Unified Inbox and each configured account Inbox.
