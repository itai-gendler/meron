---
{
  "kind": "primary",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request move to-do.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::task"
        }
      }
    },
    {
      "text": "A desktop to-do and its different destination list both exist.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::task"
        }
      }
    },
    {
      "text": "Move the selected desktop Task to the chosen existing List and update its list/order placement. The same Task belongs to the chosen List.",
      "kind": "product",
      "entities": [
        {
          "entity": "task",
          "effect": "changes",
          "facts": [
            "Order"
          ]
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::task"
        }
      },
      "actor": "user"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/tasks.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/tasks.rs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Tasks.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/TasksRouteUi.kt"
    }
  ]
}
---

# Move task — primary

## Trigger

A desktop to-do and its different destination list both exist.

## Outcome

Move the selected desktop Task to the chosen existing List and update its list/order placement. The same Task belongs to the chosen List.
