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
      "text": "Request browse to-do.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::task-list"
        },
        "android": {
          "place": "android::task-list"
        },
        "ios": {
          "place": "ios::task-list"
        }
      }
    },
    {
      "text": "The selected local list exists and its local to-dos are available.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::task-list"
        },
        "android": {
          "place": "android::task-list"
        },
        "ios": {
          "place": "ios::task-list"
        }
      }
    },
    {
      "text": "Read local Lists and the selected List Tasks, optionally including completed entries. The selected local Tasks are available; list access seeds a default only when no Lists exist.",
      "kind": "product",
      "entities": [
        {
          "entity": "task-list",
          "effect": "reads",
          "facts": [
            "Title",
            "Order"
          ]
        },
        {
          "entity": "task",
          "effect": "reads",
          "facts": [
            "Title",
            "Notes",
            "Due date",
            "Completion",
            "Order",
            "Mail reference"
          ]
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::task-list"
        },
        "android": {
          "place": "android::task-list"
        },
        "ios": {
          "place": "ios::task-list"
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

# Browse tasks — primary

## Trigger

The selected local list exists and its local to-dos are available.

## Outcome

Read local Lists and the selected List Tasks, optionally including completed entries. The selected local Tasks are available; list access seeds a default only when no Lists exist.
