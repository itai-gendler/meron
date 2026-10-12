---
{
  "kind": "edge",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request restore backup.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::backup"
        }
      }
    },
    {
      "text": "The transfer is malformed, its database transaction fails, secret-store handling fails, or the host reload fails after application.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::backup"
        }
      }
    },
    {
      "text": "Malformed/decryption/apply failure is reported without successful restore. Core database application uses one transaction and rolls back on its failure; external secret-store effects or a later host reload have separate failure boundaries, so universal restore atomicity is not asserted.",
      "kind": "product",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::backup"
        }
      },
      "actor": "user"
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/backup.rs#apply"
    }
  ]
}
---



# Restore backup — invalid or partial desktop

## Trigger

The transfer is malformed, its database transaction fails, secret-store handling fails, or the host reload fails after application.

## Outcome

Malformed/decryption/apply failure is reported without successful restore. Core database application uses one transaction and rolls back on its failure; external secret-store effects or a later host reload have separate failure boundaries, so universal restore atomicity is not asserted.
