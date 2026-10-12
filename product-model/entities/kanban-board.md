---
{
  "relations": [
    {
      "entity": "kanban-column",
      "verb": "has",
      "cardinality": "one-to-many"
    }
  ],
  "domain": "kanban-boards",
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


# Kanban board

Created, selected, configured, reordered on desktop and removed independently of backing mail/feed content.

## Information kept

- **Name** — The retained name of this board.
- **Avatar** — The image reference chosen for this board.
- **Wallpaper** — The board wallpaper choices and image references.
- **Order** — The retained order among sibling entries.
