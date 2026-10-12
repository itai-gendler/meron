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
      "text": "Choose Delete for the selected local list.",
      "kind": "actor",
      "actor": "user",
      "capability": "delete-task-list",
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
      "text": "Remove the task list and its contained Tasks while retaining the offered Undo payload.",
      "kind": "product",
      "actor": "user",
      "capability": "delete-task-list",
      "entities": [
        {
          "entity": "task-list",
          "effect": "removes",
          "as": "deleted-list"
        },
        {
          "entity": "task",
          "effect": "removes",
          "with": "deleted-list",
          "from": "Completed",
          "as": "completed-children"
        },
        {
          "entity": "task",
          "effect": "removes",
          "with": "deleted-list",
          "from": "Open",
          "as": "open-children"
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
      }
    },
    {
      "text": "Select the remaining local list.",
      "kind": "product",
      "actor": "user",
      "capability": "delete-task-list",
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
      "text": "Read the selected local list contents.",
      "kind": "actor",
      "actor": "user",
      "capability": "browse-tasks",
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
      "text": "Return the selected fallback task list and any local Task summaries remaining in it.",
      "kind": "product",
      "actor": "user",
      "capability": "browse-tasks",
      "entities": [
        {
          "entity": "task-list",
          "effect": "reads",
          "facts": [
            "Title",
            "Order"
          ],
          "as": "remaining-list"
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
          ],
          "as": "remaining-tasks"
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
      }
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


# Continue after deleting the selected local list — remaining

## Trigger

The selected local list is deleted successfully and another list remains.

## Outcome

A remaining or seeded fallback list is selected and its local contents are read.
