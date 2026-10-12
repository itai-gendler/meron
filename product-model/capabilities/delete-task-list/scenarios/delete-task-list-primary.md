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
      "text": "Request delete local list.",
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
      "text": "The selected local list is deleted successfully while a remaining list can be selected.",
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
      "text": "Remove the selected List and contained Tasks, refresh Lists, then select the remaining/default List. The removed identities can be restored through the supported Undo payload; the selected fallback list is readable.",
      "kind": "product",
      "entities": [
        {
          "entity": "task-list",
          "effect": "removes"
        },
        {
          "entity": "task",
          "effect": "removes",
          "with": "task-list",
          "from": "Completed",
          "as": "completed-children"
        },
        {
          "entity": "task",
          "effect": "removes",
          "with": "task-list",
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

# Delete task list — primary

## Trigger

The selected local list is deleted successfully while a remaining list can be selected.

## Outcome

Remove the selected List and contained Tasks, refresh Lists, then select the remaining/default List. The removed identities can be restored through the supported Undo payload; the selected fallback list is readable.
