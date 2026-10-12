---
{
  "kind": "primary",
  "routes": {
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request read shared preferences.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::general-settings"
        },
        "ios": {
          "place": "ios::general-settings"
        }
      }
    },
    {
      "text": "The native preference store or published service preferences response is available.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::general-settings"
        },
        "ios": {
          "place": "ios::general-settings"
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
        }
      ],
      "contexts": {
        "android": {
          "place": "android::general-settings"
        },
        "ios": {
          "place": "ios::general-settings"
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

# Read app settings — primary mobile

## Trigger

The native preference store or published MCP settings response is available.

## Outcome

Read the applicable current-platform preferences; MCP returns only its supported app-setting catalogue and redacts sensitive configuration. Applicable supported settings are readable without revealing opaque secrets.
