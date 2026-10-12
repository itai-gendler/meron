---
{
  "entities": [
    {
      "entity": "app-settings",
      "shows": [
        "Signature"
      ],
      "collects": [
        "Signature"
      ]
    },
    {
      "entity": "desktop-settings",
      "shows": [
        "Send shortcut",
        "Spell check",
        "Composition preferences"
      ],
      "collects": [
        "Send shortcut",
        "Spell check",
        "Composition preferences"
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


# Composer settings

Change the applicable native Composer preferences and shared signature.
