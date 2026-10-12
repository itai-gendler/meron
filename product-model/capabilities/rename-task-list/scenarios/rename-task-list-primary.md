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
      "text": "Request rename local list.",
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
      "text": "An existing local list receives a nonblank replacement title.",
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
      "text": "Persist the nonblank trimmed title of the selected List. The List retains its new title.",
      "kind": "product",
      "entities": [
        {
          "entity": "task-list",
          "effect": "changes",
          "facts": [
            "Title"
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

# Rename task list — primary

## Trigger

An existing local list receives a nonblank replacement title.

## Outcome

Persist the nonblank trimmed title of the selected List. The List retains its new title.
