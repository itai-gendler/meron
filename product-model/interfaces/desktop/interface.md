---
{
  "type": "desktop-app",
  "actors": [
    "user"
  ],
  "languages": [
    "ar",
    "de",
    "el",
    "en",
    "es",
    "et",
    "fr",
    "it",
    "ja",
    "ko",
    "lv",
    "pl",
    "pt",
    "pt-BR",
    "sv",
    "tr",
    "vi",
    "zh-Hans",
    "zh-Hant"
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/accounts.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/components/dialog/useAccountDialog.ts#useAccountDialog"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Accounts.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/protocol/accounts.rs#add_mobile_password_account"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/store/accounts.rs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/App.tsx#App"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/boot.ts#boot"
    }
  ],
  "entryPoints": [
    {
      "desktop-app": "mailto:"
    }
  ]
}
---

# Desktop

The local application for mail, feeds, Kanban, Tasks and settings, including MCP administration.
