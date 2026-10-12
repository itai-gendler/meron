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
      "entity": "mobile-settings",
      "shows": [
        "Language",
        "Tasks visible",
        "Hidden accounts",
        "Appearance preferences",
        "Checking preferences",
        "Live push preference"
      ],
      "collects": [
        "Language",
        "Tasks visible",
        "Hidden accounts",
        "Appearance preferences",
        "Checking preferences",
        "Live push preference"
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
