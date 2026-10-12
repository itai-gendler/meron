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
      "text": "Request edit to-do.",
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
      "text": "An existing local to-do receives title, notes or due-date edits.",
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
      "text": "Persist the selected Task title, notes and optional date. The selected Task retains its edited facts without implying a scheduled reminder.",
      "kind": "product",
      "entities": [
        {
          "entity": "task",
          "effect": "changes",
          "facts": [
            "Title",
            "Notes",
            "Due date"
          ]
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

# Edit task — primary

## Trigger

An existing local to-do receives title, notes or due-date edits.

## Outcome

Persist the selected Task title, notes and optional date. The selected Task retains its edited facts without implying a scheduled reminder.
