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
      "text": "Request complete to-do.",
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
      "text": "An existing local to-do is Open.",
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
      "text": "Persist completion for the selected open Task. The Task is Completed and participates in completed filtering/clearing.",
      "kind": "product",
      "entities": [
        {
          "entity": "task",
          "effect": "changes",
          "facts": [
            "Completion"
          ],
          "from": "Open",
          "to": "Completed"
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

# Complete task — primary

## Trigger

An existing local to-do is Open.

## Outcome

Persist completion for the selected open Task. The Task is Completed and participates in completed filtering/clearing.
