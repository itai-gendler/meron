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
      "text": "Choose Create.",
      "kind": "actor",
      "actor": "user",
      "capability": "create-board",
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
      "text": "Create the kanban board with the native default source columns.",
      "kind": "product",
      "actor": "user",
      "capability": "create-board",
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
      }
    },
    {
      "text": "Select the newly created board for editing its board configuration.",
      "kind": "product",
      "actor": "user",
      "capability": "create-board",
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
      "text": "Edit the selected board name or media choices.",
      "kind": "actor",
      "actor": "user",
      "capability": "change-board-settings",
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
      "text": "Retain the changed kanban board name or supported media choices.",
      "kind": "product",
      "actor": "user",
      "capability": "change-board-settings",
      "entities": [
        {
          "entity": "kanban-board",
          "effect": "changes",
          "facts": [
            "Name",
            "Avatar",
            "Wallpaper"
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
    }
  ]
}
---


# Work with the newly selected board — settings

## Trigger

Native board creation succeeds and selects the new board.

## Outcome

The new board is selected for reading or configuration.

## Decision points

### Initial sources

Which native creation handler supplies the default columns?

- Desktop → the initial column reads Unified Inbox.
- Android or iOS → the initial columns read Unified Inbox and each configured account Inbox.
