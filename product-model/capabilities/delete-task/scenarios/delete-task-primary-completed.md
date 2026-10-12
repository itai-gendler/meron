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
      "text": "Request delete to-do.",
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
      "text": "An existing local to-do is selected for deletion.",
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
      "text": "Remove the selected local Task and retain the supported restoration payload for the offered Undo. The selected Task is removed; supported Undo can restore its retained facts.",
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

# Delete task — primary — completed

## Trigger

The selected to-do is Completed. An existing local to-do is selected for deletion.

## Outcome

Remove the selected local Task and retain the supported restoration payload for the offered Undo. The selected Task is removed; supported Undo can restore its retained facts.
