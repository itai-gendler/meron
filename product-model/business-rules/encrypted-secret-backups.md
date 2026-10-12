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

# Secret-bearing exports require passphrase encryption

Ordinary exports omit credentials. Selecting secrets requires a nonempty passphrase and encrypts the payload. A wrong passphrase fails before unreadable contents apply and is retryable. This transfer encryption is not encryption of every local file.
