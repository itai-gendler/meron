---
{
  "kind": "primary",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request change general settings.",
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
      "text": "The applicable general preference values match the platform’s supported types.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::general-settings"
        }
      }
    },
    {
      "text": "Apply the selected supported General field to the current native platform; MCP only changes its enumerated desktop preference subset and never account proxies/checking settings. The applicable selected preference is retained; desktop/mobile field sets remain distinct.",
      "kind": "product",
      "entities": [
        {
          "entity": "desktop-settings",
          "effect": "changes",
          "facts": [
            "Language",
            "Tasks visible",
            "Hidden accounts",
            "Real avatars",
            "Unread badges",
            "Unified inbox visibility",
            "Interface font",
            "Appearance preferences"
          ]
        },
        {
          "entity": "app-settings",
          "effect": "changes",
          "facts": [
            "Proxy"
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


# Change general settings — primary desktop

## Trigger

The applicable general preference values match the platform’s supported types.

## Outcome

Apply the selected supported General field to the current native platform; MCP only changes its enumerated desktop preference subset and never account proxies/checking settings. The applicable selected preference is retained; desktop/mobile field sets remain distinct.
