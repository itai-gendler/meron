---
{
  "kind": "primary",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request read shared preferences.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::general-settings"
        }
      }
    },
    {
      "text": "The native preference store or published service preferences response is available.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::general-settings"
        }
      }
    },
    {
      "text": "Read the applicable current-platform preferences; MCP returns only its supported app-setting catalogue and redacts sensitive configuration. Applicable supported settings are readable without revealing opaque secrets.",
      "kind": "product",
      "entities": [
        {
          "entity": "app-settings",
          "effect": "reads",
          "facts": [
            "Signature",
            "Proxy"
          ]
        },
        {
          "entity": "desktop-settings",
          "effect": "reads",
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
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::general-settings"
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
    }
  ]
}
---

# Read app settings — primary desktop

## Trigger

The native preference store or published MCP settings response is available.

## Outcome

Read the applicable current-platform preferences; MCP returns only its supported app-setting catalogue and redacts sensitive configuration. Applicable supported settings are readable without revealing opaque secrets.
