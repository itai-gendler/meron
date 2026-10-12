---
{
  "kind": "primary",
  "result": "achieved",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Choose Remove for the selected board.",
      "kind": "actor",
      "actor": "user",
      "capability": "remove-board",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::kanban-board"
        }
      }
    },
    {
      "text": "Remove the kanban board and its columns while retaining all backing content.",
      "kind": "product",
      "actor": "user",
      "capability": "remove-board",
      "entities": [
        {
          "entity": "kanban-board",
          "effect": "removes",
          "as": "removed-board"
        },
        {
          "entity": "kanban-column",
          "effect": "removes",
          "with": "removed-board",
          "as": "removed-columns"
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::kanban-board"
        }
      }
    },
    {
      "text": "Select the restored desktop Mail context.",
      "kind": "product",
      "actor": "user",
      "capability": "remove-board",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        }
      }
    },
    {
      "text": "Read the selected mailbox results.",
      "kind": "actor",
      "actor": "user",
      "capability": "browse-messages",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        }
      }
    },
    {
      "text": "Return the folder choices and available email summaries for the selected mailbox.",
      "kind": "product",
      "actor": "user",
      "capability": "browse-messages",
      "entities": [
        {
          "entity": "folder",
          "effect": "reads",
          "facts": [
            "Name",
            "Hierarchy",
            "Role",
            "Unread count"
          ]
        },
        {
          "entity": "email-message",
          "effect": "reads",
          "facts": [
            "Location",
            "Sender",
            "Recipients",
            "Subject",
            "Date",
            "Unread",
            "Starred",
            "Body availability"
          ]
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        }
      }
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mail.go#threadRead"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/mail.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/mailFlags.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/thread_read.rs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Mail.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Thread.kt"
    }
  ]
}
---



# Continue after removing the selected board — desktop mail fallback

## Trigger

Removal of the selected board succeeds and desktop restores its Mail fallback.

## Outcome

The Product selects a remaining board or the desktop Mail fallback and that source is read.
