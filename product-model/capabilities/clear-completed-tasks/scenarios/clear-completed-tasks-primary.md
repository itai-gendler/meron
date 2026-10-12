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
      "text": "Request clear completed to-do.",
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
      "text": "The selected local list contains completed to-dos.",
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
      "text": "Remove completed Tasks from the selected List and offer the supported restoration payload. Completed entries are removed while open entries remain.",
      "kind": "product",
      "entities": [
        {
          "entity": "task",
          "effect": "removes",
          "from": "Completed"
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

# Clear completed tasks — primary

## Trigger

The selected local list contains completed to-dos.

## Outcome

Remove completed Tasks from the selected List and offer the supported restoration payload. Completed entries are removed while open entries remain.
