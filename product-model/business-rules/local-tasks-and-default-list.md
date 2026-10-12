---
{
  "appliesTo": [
    {
      "type": "capability",
      "id": "browse-tasks"
    },
    {
      "type": "capability",
      "id": "create-task"
    },
    {
      "type": "capability",
      "id": "edit-task"
    },
    {
      "type": "capability",
      "id": "delete-task"
    },
    {
      "type": "capability",
      "id": "restore-tasks"
    },
    {
      "type": "capability",
      "id": "delete-task-list"
    },
    {
      "type": "capability",
      "id": "clear-completed-tasks"
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

# Tasks remain local and preserve conditional references and restoration

Lists/Tasks persist locally. Reading no lists seeds My Tasks. List removal removes its Tasks; restoring original identities can leave intervening defaults. Mail references can become stale. Mobile failures can silently retain previous information. Tasks visibility gates navigation, not ownership; no synchronization or due-date reminder service is established.
