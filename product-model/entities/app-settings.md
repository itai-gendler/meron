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


# App settings

Shared core configuration; proxy credentials are not MCP disclosure.

## Information kept

- **Signature** — The app-wide signature HTML followed by accounts configured to use it.
- **Proxy** — The app-wide outbound proxy configuration; secrets are not MCP disclosure.
