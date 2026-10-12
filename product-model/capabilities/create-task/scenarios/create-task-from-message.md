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
      "text": "Request create to-do.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::task"
        },
        "android": {
          "place": "android::task"
        },
        "ios": {
          "place": "ios::task"
        }
      }
    },
    {
      "text": "Create to-do is chosen from selected mail.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::task"
        },
        "android": {
          "place": "android::task"
        },
        "ios": {
          "place": "ios::task"
        }
      }
    },
    {
      "text": "The new local to-do retains its derived title and supported mail reference, which can become stale.",
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
          "to": "Open"
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::task"
        },
        "android": {
          "place": "android::task"
        },
        "ios": {
          "place": "ios::task"
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

# Create task — from message

## Trigger

Create to-do is chosen from selected mail.

## Outcome

The new local to-do retains its derived title and supported mail reference, which can become stale.
