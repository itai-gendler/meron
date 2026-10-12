---
{
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

# Kanban column

Added, changed, reordered and removed under a board. Unified is a readable source, not a writable destination.

## Information kept

- **Source account** — The configured mail/feed account or Unified source selection.
- **Folder selection** — The selected backing mailbox/folder source.
- **Filter** — The column filter selection.
- **Attachments only** — Whether the column selects attachment-bearing results only.
- **Order** — The retained order among sibling entries.
