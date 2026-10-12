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
      "text": "The native restoration payload retains deleted to-do identities and the restore succeeds.",
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
      "text": "Reinsert the deleted Task identities/facts from the supported restoration payload without erasing unrelated entries. Restored Tasks retain their original completion/order and references according to the payload.",
      "kind": "product",
      "entities": [
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

# Restore tasks — primary

## Trigger

The native restoration payload retains deleted to-do identities and the restore succeeds.

## Outcome

Reinsert the deleted Task identities/facts from the supported restoration payload without erasing unrelated entries. Restored Tasks retain their original completion/order and references according to the payload.
