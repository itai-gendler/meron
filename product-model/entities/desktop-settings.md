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

# Desktop settings

MCP exposes only its enumerated subset.

## Information kept

- **Language** — The selected shipped locale.
- **Tasks visible** — The preference controlling Tasks navigation visibility, not core Task ownership.
- **Hidden accounts** — Account selections hidden from native navigation.
- **Conversation layout** — The chat or traditional presentation choice.
- **Send shortcut** — The supported quick-reply sending shortcut choice.
- **Spell check** — The desktop composition spell-check preference.
- **Real avatars** — The preference for real sender avatars.
- **Unread badges** — The account unread-badge preference.
- **Unified inbox visibility** — The native unified-inbox navigation preference.
- **Interface font** — The interface font selection.
- **Message font** — The message font selection.
- **Appearance preferences** — The inspected native appearance preferences.
- **Composition preferences** — The inspected native composition preferences.
- **Saved selection** — The desktop persisted active account/folder/board selection.
