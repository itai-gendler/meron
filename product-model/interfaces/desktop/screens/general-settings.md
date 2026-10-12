---
{
  "entities": [
    {
      "entity": "app-settings",
      "shows": [
        "Proxy"
      ],
      "collects": [
        "Proxy"
      ]
    },
    {
      "entity": "desktop-settings",
      "shows": [
        "Language",
        "Tasks visible",
        "Hidden accounts",
        "Real avatars",
        "Unread badges",
        "Unified inbox visibility",
        "Interface font",
        "Appearance preferences"
      ],
      "collects": [
        "Language",
        "Tasks visible",
        "Hidden accounts",
        "Real avatars",
        "Unread badges",
        "Unified inbox visibility",
        "Interface font",
        "Appearance preferences"
      ]
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


# General settings

Change the applicable native General preferences, proxy configuration and local storage controls.
