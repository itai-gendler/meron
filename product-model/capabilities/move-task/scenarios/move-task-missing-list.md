---
{
  "kind": "validation",
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
      "text": "The destination local list no longer exists.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::task"
        }
      }
    },
    {
      "text": "Movement fails without successful destination assignment.",
      "kind": "product",
      "entities": [],
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

# Move task — missing list

## Trigger

The destination local list no longer exists.

## Outcome

Movement fails without successful destination assignment.
