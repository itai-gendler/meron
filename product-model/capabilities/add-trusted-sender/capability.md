---
{
  "availability": [
    {
      "place": "desktop"
    },
    {
      "place": "android"
    },
    {
      "place": "ios"
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
  ],
  "domain": "messages"
}
---

# Add trusted sender

Normalize and persist the selected sender address in the app-wide remote-content allowlist. The sender has a retained allowlist entry used by subsequent remote-content preparation.
