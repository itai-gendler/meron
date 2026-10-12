---
{
  "appliesTo": [
    {
      "type": "capability",
      "id": "create-folder"
    },
    {
      "type": "capability",
      "id": "delete-folder"
    },
    {
      "type": "capability",
      "id": "enable-folder-notifications"
    },
    {
      "type": "capability",
      "id": "disable-folder-notifications"
    },
    {
      "type": "capability",
      "id": "empty-folder"
    }
  ],
  "references": [
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

# Protected folders and exact emptying roles constrain deletion

Deletion checks the actual subtree special roles and can fail after partial removal. Optional folder notifications apply only where offered. Native emptying permits Trash/Junk; MCP emptying is Trash-only and uses a frozen exact snapshot. No kept eligibility boolean is assumed.
