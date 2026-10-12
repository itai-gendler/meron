---
{
  "kind": "alternative",
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
      "text": "Deletion leaves no local list.",
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
      "text": "A subsequent list read seeds another My Tasks and selects the fallback.",
      "kind": "product",
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
        },
        {
          "entity": "task-list",
          "effect": "creates",
          "facts": [
            "Title",
            "Order"
          ],
          "as": "replacement-list"
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

# Delete task list — default recreated

## Trigger

Deletion leaves no local list.

## Outcome

A subsequent list read seeds another My Tasks and selects the fallback.
