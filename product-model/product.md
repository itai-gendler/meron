---
{
  "id": "meron",
  "summary": "Mail, RSS/Atom, folder-backed Kanban and local Tasks on desktop, Android and iOS, with optional local desktop MCP access.",
  "category": "email-client",
  "tags": [
    "email",
    "rss",
    "kanban",
    "tasks"
  ],
  "authors": [
    {
      "name": "Nonbili Inc."
    }
  ],
  "license": "AGPL-3.0-or-later",
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
  "limitations": [
    "Tasks are local; they do not synchronize with a task server.",
    "Kanban cards project backing mail or feeds; removing a board does not delete them.",
    "SMTP acceptance does not establish recipient delivery.",
    "Backups transfer configuration and Tasks, not cached mailbox bodies or attachment assets.",
    "Send retry payloads, MCP operations and recent activity are bounded process memory."
  ],
  "references": [
    {
      "kind": "code",
      "role": "context",
      "target": "metadata/flatpak/jp.nonbili.meron.metainfo.xml"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/App.tsx"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronApp.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_tools.go"
    }
  ]
}
---

# Meron

Meron connects mail accounts and RSS/Atom subscriptions on desktop, Android and iOS. People read conversations or individual messages, compose and send mail, organize conversations through folder-backed Kanban boards, and maintain local Tasks. Desktop optionally exposes selected mail, feed and configuration abilities through a local MCP client contract.
