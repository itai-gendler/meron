---
{
  "relations": [
    {
      "entity": "task",
      "verb": "contains",
      "cardinality": "one-to-many"
    }
  ],
  "domain": "tasks",
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


# Task list

Created, renamed, removed with its Tasks and restored. Reading lists when none exist seeds “My Tasks.”

## Information kept

- **Title** — The retained name of this local list.
- **Order** — The retained order among sibling entries.
