---
{
  "singleton": true,
  "domain": "general",
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

# Mobile settings

Shared mobile preference facts do not imply identical host outcomes.

## Information kept

- **Language** — The selected shipped locale.
- **Tasks visible** — The preference controlling Tasks navigation visibility, not core Task ownership.
- **Hidden accounts** — Account selections hidden from native navigation.
- **Conversation layout** — The chat or traditional presentation choice.
- **Appearance preferences** — The inspected native appearance preferences.
- **Composition preferences** — The inspected native composition preferences.
- **Checking preferences** — The mobile mail-checking preference values.
- **Live push preference** — The mobile live-push preference, subject to native service behavior.
- **Saved board** — The persisted selected mobile board.
