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
      "text": "Request remove column.",
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
      "text": "A retained column definition is selected for removal.",
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
      "text": "Remove the selected configured column from the board. The column definition is gone; backing mail/subscription content remains.",
      "kind": "product",
      "entities": [
        {
          "entity": "kanban-column",
          "effect": "removes"
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

# Remove column — primary

## Trigger

A retained column definition is selected for removal.

## Outcome

Remove the selected configured column from the board. The column definition is gone; backing mail/feed content remains.
