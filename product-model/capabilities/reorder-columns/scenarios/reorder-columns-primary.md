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
      "text": "Request reorder columns.",
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
      "text": "The retained columns are supplied in their new order.",
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
      "text": "Persist the new order of columns within the selected board. The selected board retains the column order.",
      "kind": "product",
      "entities": [
        {
          "entity": "kanban-column",
          "effect": "changes",
          "facts": [
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
    }
  ]
}
---

# Reorder columns — primary

## Trigger

The retained columns are supplied in their new order.

## Outcome

Persist the new order of columns within the selected board. The selected board retains the column order.
