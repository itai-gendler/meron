---
{
  "kind": "primary",
  "routes": {
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request export backup.",
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
      "text": "Configuration and local to-do export is selected without secrets and host publication succeeds.",
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
      "text": "Collect account/subscription/settings/Task configuration without secrets or cached message/media bodies, serialize and export it. The configuration/Task backup is exported when host writing succeeds.",
      "kind": "product",
      "entities": [
        {
          "entity": "mail-account",
          "effect": "reads",
          "facts": [
            "Address",
            "Display name",
            "Sender name",
            "Provider",
            "Connection configuration",
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
          "effect": "reads",
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
          "effect": "reads",
          "facts": [
            "URL",
            "Title"
          ]
        },
        {
          "entity": "task-list",
          "effect": "reads",
          "facts": [
            "Title",
            "Order"
          ]
        },
        {
          "entity": "task",
          "effect": "reads",
          "facts": [
            "Title",
            "Notes",
            "Due date",
            "Completion",
            "Order",
            "Mail reference"
          ]
        },
        {
          "entity": "app-settings",
          "effect": "reads",
          "facts": [
            "Signature",
            "Proxy"
          ]
        },
        {
          "entity": "mobile-settings",
          "effect": "reads",
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
          "effect": "reads",
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
      "target": "meron-core/src/backup.rs#collect"
    }
  ]
}
---


# Export backup — primary mobile

## Trigger

Configuration and local to-do export is selected without secrets and host publication succeeds.

## Outcome

Collect account/subscription/settings/Task configuration without secrets or cached message/media bodies, serialize and export it. The configuration/Task backup is exported when host writing succeeds.
