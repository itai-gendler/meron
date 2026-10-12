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
      "text": "Request restore to-do.",
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
      "text": "Restoration includes a deleted local list.",
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
      "text": "The original list and to-do identities are restored without removing intervening defaults.",
      "kind": "product",
      "entities": [
        {
          "entity": "task-list",
          "effect": "creates",
          "facts": [
            "Title",
            "Order"
          ]
        },
        {
          "entity": "task",
          "effect": "creates",
          "facts": [
            "Title",
            "Notes",
            "Due date",
            "Completion",
            "Order",
            "Mail reference"
          ],
          "to": "Completed",
          "with": "task-list",
          "as": "restored-completed"
        },
        {
          "entity": "task",
          "effect": "creates",
          "facts": [
            "Title",
            "Notes",
            "Due date",
            "Completion",
            "Order",
            "Mail reference"
          ],
          "to": "Open",
          "with": "task-list",
          "as": "restored-open"
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

# Restore tasks — with list

## Trigger

Restoration includes a deleted local list.

## Outcome

The original list and to-do identities are restored without removing intervening defaults.
