---
{
  "kind": "edge",
  "routes": {
    "desktop": "Desktop",
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request browse board.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::kanban-board"
        },
        "android": {
          "place": "android::kanban-board"
        },
        "ios": {
          "place": "ios::kanban-board"
        }
      }
    },
    {
      "text": "One backing column cannot load.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::kanban-board"
        },
        "android": {
          "place": "android::kanban-board"
        },
        "ios": {
          "place": "ios::kanban-board"
        }
      }
    },
    {
      "text": "Loaded columns can remain while the failed column retains its error.",
      "kind": "product",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::kanban-board"
        },
        "android": {
          "place": "android::kanban-board"
        },
        "ios": {
          "place": "ios::kanban-board"
        }
      },
      "actor": "user"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/kanban.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/lib/kanbanData.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Kanban.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/KanbanUi.kt"
    }
  ]
}
---

# Browse board — column failure

## Trigger

One backing column cannot load.

## Outcome

Loaded columns can remain while the failed column retains its error.
