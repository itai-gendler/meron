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
      "text": "Request reopen to-do.",
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
      "text": "An existing local to-do is Completed.",
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
      "text": "Clear completion for the selected completed Task. The Task returns to Open.",
      "kind": "product",
      "entities": [
        {
          "entity": "task",
          "effect": "changes",
          "facts": [
            "Completion"
          ],
          "from": "Completed",
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

# Reopen task — primary

## Trigger

An existing local to-do is Completed.

## Outcome

Clear completion for the selected completed Task. The Task returns to Open.
