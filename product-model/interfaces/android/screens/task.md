---
{
  "entities": [
    {
      "entity": "task",
      "shows": [
        "Title",
        "Notes",
        "Due date",
        "Completion",
        "Order",
        "Mail reference"
      ],
      "collects": [
        "Title",
        "Notes",
        "Due date"
      ]
    },
    {
      "entity": "task-list",
      "shows": [
        "Title"
      ]
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


# Task

Read and edit the selected Task; desktop also offers movement between Lists.
