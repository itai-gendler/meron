---
{
  "availability": [
    {
      "place": "desktop"
    },
    {
      "place": "android"
    },
    {
      "place": "ios"
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
  ],
  "domain": "kanban-boards"
}
---

# Create board

Persist a new named board with its supported defaults and select the created board. The newly selected board is ready for reading/configuration; default columns follow the native creation path.
