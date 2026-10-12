---
{
  "appliesTo": [
    {
      "type": "capability",
      "id": "read-account-configurations"
    },
    {
      "type": "capability",
      "id": "read-app-settings"
    },
    {
      "type": "capability",
      "id": "change-mail-account-settings"
    },
    {
      "type": "capability",
      "id": "change-feed-account-settings"
    },
    {
      "type": "capability",
      "id": "change-general-settings"
    },
    {
      "type": "capability",
      "id": "change-message-settings"
    },
    {
      "type": "capability",
      "id": "change-composer-settings"
    },
    {
      "type": "capability",
      "id": "read-configuration-capabilities"
    }
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
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/feeds.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/rss.rs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/rss/opml.rs"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Mailbox.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_tools.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_configuration.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_mutations.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_operations.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/mcp_mail.rs"
    }
  ]
}
---

# Configuration tools accept only published nonsecret controls

App keys are signature, send_shortcut, conversation_layout, spell_check, show_real_avatars, show_unread_account_badge, show_unified_inbox_in_sidenav, font_family and message_font_family. Account keys are display_name, sender_name, aliases, signature, load_remote_images, conversation_html, included_in_unified, muted, paused and save_sent_copy. Meaningful feed subsets exclude mail-only behavior. Types/enumerations apply. Signatures are at most 256 KiB and rejected if allowlist sanitization would change their HTML. Configuration reads redact tokens/passwords/proxy credentials; management grants remain independent of mail grants.
