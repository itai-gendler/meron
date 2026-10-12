---
{
  "kind": "primary",
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
      "text": "A supported parseable transfer applies successfully through its database transaction and host reload.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::backup"
        }
      }
    },
    {
      "text": "Parse the selected backup, skip existing account identities, apply supported settings and merge local Lists/Tasks/subscriptions by their identities. The supported imported configuration is retained; transfer does not promise universal atomicity or portable media assets.",
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
          "entity": "desktop-settings",
          "effect": "changes",
          "facts": [
            "Language",
            "Tasks visible",
            "Hidden accounts",
            "Conversation layout",
            "Send shortcut",
            "Spell check",
            "Real avatars",
            "Unread badges",
            "Unified inbox visibility",
            "Interface font",
            "Message font",
            "Appearance preferences",
            "Composition preferences",
            "Saved selection"
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


# Restore backup — primary desktop

## Trigger

A supported parseable transfer applies successfully through its database transaction and host reload.

## Outcome

Parse the selected backup, skip existing account identities, apply supported settings and merge local Lists/Tasks/subscriptions by their identities. The supported imported configuration is retained; transfer does not promise universal atomicity or portable media assets.
