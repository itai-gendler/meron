---
{
  "appliesTo": [
    {
      "type": "capability",
      "id": "export-backup"
    },
    {
      "type": "capability",
      "id": "restore-backup"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/settings.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/components/dialog/SettingsDialog.tsx"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/SettingsUi.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/shared/src/commonMain/kotlin/jp/nonbili/meron/shared/RemoteContent.kt"
    }
  ]
}
---

# Transfers apply their supported configuration and identity merge

Payloads transfer inspected account/settings/subscription/Task sections. Existing identities are skipped/merged as implemented and preference keys apply through their supported sections. Core database application is transactional: an apply failure rolls back those database changes. External secret storage and later host reload are separate boundaries, so universal restore atomicity is not asserted. Referenced avatars/wallpapers and platform preferences do not establish portable assets or universal cross-platform interpretation.
