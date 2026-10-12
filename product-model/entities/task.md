---
{
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


# Task

States Open, Completed. Created, edited, reordered, completed/reopened, deleted/restored; moved between lists on desktop. Mail references can remain stale.

## Information kept

- **Title** — The retained title of this local Task.
- **Notes** — The retained Task notes.
- **Due date** — The retained optional Task date; this does not schedule a reminder service.
- **Completion** — Whether the Task is open or completed.
- **Order** — The retained order among sibling entries.
- **Mail reference** — The retained optional composite mail/conversation reference, which may be stale.

## States

### Open

A Task that is not completed.

### Completed

The local to-do is marked completed.
