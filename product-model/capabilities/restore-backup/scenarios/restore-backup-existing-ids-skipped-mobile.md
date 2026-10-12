---
{
  "kind": "alternative",
  "routes": {
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request restore backup.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::backup"
        },
        "ios": {
          "place": "ios::backup"
        }
      }
    },
    {
      "text": "Imported data overlap retained identities.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::backup"
        },
        "ios": {
          "place": "ios::backup"
        }
      }
    },
    {
      "text": "Existing identities are skipped/merged according to their payload section and supported preferences are applied.",
      "kind": "product",
      "entities": [
        {
          "entity": "mail-account",
          "effect": "creates",
          "facts": [
            "Address",
            "Display name",
            "Sender name",
            "Provider",
            "Connection configuration",
            "Credentials",
            "Credential availability",
            "Needs reconnect",
            "Certificate trust",
            "Signature",
            "Load remote images",
            "Conversation HTML",
            "Unified inclusion",
            "Muted",
            "Paused",
            "Save sent copy",
            "Order",
            "Avatar",
            "Wallpaper"
          ]
        },
        {
          "entity": "feed-account",
          "effect": "creates",
          "facts": [
            "Display name",
            "Load remote images",
            "Conversation HTML",
            "Unified inclusion",
            "Muted",
            "Paused",
            "Polling interval",
            "Order",
            "Avatar",
            "Wallpaper"
          ]
        },
        {
          "entity": "feed",
          "effect": "creates",
          "facts": [
            "URL",
            "Title",
            "Synchronization information",
            "Error"
          ],
          "with": "feed-account"
        },
        {
          "entity": "task-list",
          "effect": "creates",
          "facts": [
            "Title",
            "Order"
          ]
        },
        {
          "entity": "task",
          "effect": "creates",
          "facts": [
            "Title",
            "Notes",
            "Due date",
            "Completion",
            "Order",
            "Mail reference"
          ],
          "to": "Completed",
          "as": "restored-completed",
          "with": "task-list"
        },
        {
          "entity": "task",
          "effect": "creates",
          "facts": [
            "Title",
            "Notes",
            "Due date",
            "Completion",
            "Order",
            "Mail reference"
          ],
          "to": "Open",
          "as": "restored-open",
          "with": "task-list"
        },
        {
          "entity": "app-settings",
          "effect": "changes",
          "facts": [
            "Signature",
            "Proxy"
          ]
        },
        {
          "entity": "mobile-settings",
          "effect": "changes",
          "facts": [
            "Language",
            "Tasks visible",
            "Hidden accounts",
            "Conversation layout",
            "Appearance preferences",
            "Composition preferences",
            "Checking preferences",
            "Live push preference",
            "Saved board"
          ]
        },
        {
          "entity": "account-alias",
          "effect": "creates",
          "with": "mail-account",
          "facts": [
            "Address",
            "Display name"
          ]
        }
      ],
      "contexts": {
        "android": {
          "place": "android::backup"
        },
        "ios": {
          "place": "ios::backup"
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


# Restore backup — existing ids skipped mobile

## Trigger

Imported data overlap retained identities.

## Outcome

Existing identities are skipped/merged according to their payload section and supported preferences are applied.
