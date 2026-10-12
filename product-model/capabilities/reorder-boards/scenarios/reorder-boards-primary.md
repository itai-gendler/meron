---
{
  "kind": "primary",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request reorder boards.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::kanban-board"
        }
      }
    },
    {
      "text": "Existing desktop boards are supplied in their new order.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::kanban-board"
        }
      }
    },
    {
      "text": "Persist the reordered desktop board definitions. The boards retain the chosen order.",
      "kind": "product",
      "entities": [
        {
          "entity": "kanban-board",
          "effect": "changes",
          "facts": [
            "Order"
          ]
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::kanban-board"
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

# Reorder boards — primary

## Trigger

Existing desktop boards are supplied in their new order.

## Outcome

Persist the reordered desktop board definitions. The boards retain the chosen order.
