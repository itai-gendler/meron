---
{
  "scope": "Native desktop, Android and iOS application paths, generic desktop MCP, inspected OAuth callbacks, and their shared core persistence and protocol handlers at ea6a724a5d120b43a4e2d2337acf359ae084d26b.",
  "method": "Static inspection from entry points through handlers, persistence, authorization and observable outcomes; supporting documentation and selected test source used as leads.",
  "covered": [
    {
      "description": "Native boot, selected account/board routing and native host entry handlers.",
      "paths": [
        "desktop/frontend/src/App.tsx",
        "desktop/frontend/src/boot.ts",
        "desktop/frontend/src/states/kanban.ts",
        "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronApp.kt",
        "mobile/android/src/main/java/jp/nonbili/meron/ComposeMainActivity.kt"
      ]
    },
    {
      "description": "Account configuration, server editing, credential persistence, certificate trust and account-removal handlers.",
      "paths": [
        "desktop/accounts.go",
        "desktop/frontend/src/states/accounts.ts",
        "desktop/frontend/src/components/dialog/useAccountDialog.ts",
        "meron-core/src/protocol/accounts.rs",
        "meron-core/src/store/accounts.rs",
        "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Accounts.kt"
      ]
    },
    {
      "description": "Desktop redirect listener and shared mobile callback validation/token-exchange callers.",
      "paths": [
        "desktop/oauth.go",
        "mobile/shared/src/commonMain/kotlin/jp/nonbili/meron/shared/OAuthFlow.kt",
        "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+OAuth.kt"
      ]
    },
    {
      "description": "Mail summary/grouped-content reads, flags, folder and movement callers and core protocol/store dispatch.",
      "paths": [
        "desktop/mail.go",
        "desktop/frontend/src/states/mail.ts",
        "desktop/frontend/src/states/mailFlags.ts",
        "desktop/frontend/src/states/mailFolders.ts",
        "desktop/frontend/src/states/mailMoves.ts",
        "meron-core/src/thread_read.rs",
        "meron-core/src/unified.rs",
        "meron-core/src/mail_model.rs",
        "meron-core/src/store/threads.rs",
        "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Mail.kt",
        "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Thread.kt",
        "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+ThreadMoves.kt"
      ]
    },
    {
      "description": "Native composition, quick replies, optimistic sends and core Draft/Sent append coordination.",
      "paths": [
        "desktop/frontend/src/states/compose.ts",
        "desktop/frontend/src/states/quickReplySend.ts",
        "desktop/frontend/src/states/pendingSends.ts",
        "meron-core/src/sidecar/dispatch/compose.rs",
        "meron-core/src/engine/append.rs",
        "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Compose.kt",
        "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+QuickReply.kt"
      ]
    },
    {
      "description": "Board definitions, source projections, native Kanban selections and settings callers.",
      "paths": [
        "desktop/frontend/src/states/kanban.ts",
        "desktop/frontend/src/lib/kanbanData.ts",
        "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Kanban.kt"
      ]
    },
    {
      "description": "Feed and OPML handlers and cached feed persistence.",
      "paths": [
        "desktop/frontend/src/states/feeds.ts",
        "meron-core/src/rss.rs",
        "meron-core/src/rss/opml.rs",
        "meron-core/src/store/rss.rs"
      ]
    },
    {
      "description": "Local Task/List state, core lifecycle/restoration store and native task editing callers.",
      "paths": [
        "meron-core/src/tasks.rs",
        "desktop/frontend/src/states/tasks.ts",
        "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Tasks.kt",
        "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/TasksRouteUi.kt"
      ]
    },
    {
      "description": "Native settings, trusted remote senders and shared remote-content preparation.",
      "paths": [
        "desktop/frontend/src/states/settings.ts",
        "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/SettingsUi.kt",
        "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/RemoteSendersSettingsUi.kt",
        "mobile/shared/src/commonMain/kotlin/jp/nonbili/meron/shared/RemoteContent.kt"
      ]
    },
    {
      "description": "File handoffs, original-message export and native print preparation adapters.",
      "paths": [
        "desktop/paste_image.go",
        "desktop/eml_export.go",
        "desktop/frontend/src/lib/printMail.ts",
        "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/PlatformServices.kt"
      ]
    },
    {
      "description": "Backup transfer and native cache/storage callers.",
      "paths": [
        "meron-core/src/backup.rs",
        "desktop/paths.go",
        "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Backup.kt"
      ]
    },
    {
      "description": "MCP loopback transport, tool registration, configuration, mutation snapshots, operation retention and native administration UI.",
      "paths": [
        "desktop/mcp.go",
        "desktop/mcp_tools.go",
        "desktop/mcp_configuration.go",
        "desktop/mcp_mutations.go",
        "desktop/mcp_operations.go",
        "meron-core/src/mcp_mail.rs",
        "desktop/frontend/src/components/dialog/McpSettingsPanel.tsx"
      ]
    },
    {
      "description": "Inspected automatic checking continuations and native locale selection paths.",
      "paths": [
        "mobile/shared/src/commonMain/kotlin/jp/nonbili/meron/shared/BackgroundRefresh.kt",
        "locales/",
        "meron-core/src/engine/sync.rs",
        "meron-core/src/engine/background_sync.rs"
      ]
    }
  ],
  "exclusions": [
    {
      "description": "Development, release, packaging and hook infrastructure.",
      "paths": [
        ".github/",
        ".githooks/",
        "scripts/",
        "snap/",
        "metadata/"
      ]
    },
    {
      "description": "Design screenshots and release artwork without inspected application behavior.",
      "paths": [
        "screenshots/",
        "mobile/fastlane-config/assets/"
      ]
    }
  ],
  "unmapped": [
    {
      "description": "Complete widget setup, rendering, refresh and snapshot-privacy behavior.",
      "paths": [
        "mobile/android/src/main/java/jp/nonbili/meron/AndroidUnreadWidget.kt",
        "mobile/android/src/main/java/jp/nonbili/meron/AndroidUnreadWidgetConfigureActivity.kt",
        "mobile/ios/MeronWidgets/",
        "mobile/ios/WidgetShared/",
        "mobile/ios/Meron/IosUnreadWidgets.swift"
      ]
    },
    {
      "description": "Complete notification action/retry/Undo and OS scheduling/permission branches.",
      "paths": [
        "mobile/android/src/main/java/jp/nonbili/meron/AndroidNotificationActions.kt",
        "mobile/android/src/main/java/jp/nonbili/meron/AndroidNotificationService.kt",
        "mobile/android/src/main/java/jp/nonbili/meron/AndroidBackgroundSync.kt",
        "mobile/ios/Meron/IosBackgroundRefresh.swift"
      ]
    },
    {
      "description": "Updater, tray/window integration and complete keyboard-shortcut customization.",
      "paths": [
        "desktop/update.go",
        "desktop/frontend/src/lib/shortcuts.ts"
      ]
    },
    {
      "description": "Diagnostic and crash-log viewing, sharing and retention.",
      "paths": [
        "mobile/android/src/main/java/jp/nonbili/meron/AndroidCrashLog.kt",
        "mobile/android/src/main/java/jp/nonbili/meron/AndroidSyncDiagnosticLog.kt",
        "mobile/ios/Meron/IosSyncDiagnosticLog.swift"
      ]
    },
    {
      "description": "Complete contact/avatar resolution, composer acquisition/paste and custom-theme editing.",
      "paths": [
        "meron-core/src/avatar.rs",
        "meron-core/src/store/contacts.rs",
        "desktop/frontend/src/lib/contacts.ts",
        "desktop/frontend/src/components/dialog/ThemeEditorDialog.tsx",
        "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/CustomThemes.kt"
      ]
    },
    {
      "description": "Every provider discovery/token recovery branch and historical-store/threading/server fallback matrix.",
      "paths": [
        "desktop/oauth.go",
        "meron-core/src/protocol/",
        "meron-core/src/store/",
        "meron-core/src/engine/",
        "mobile/shared/src/commonMain/kotlin/jp/nonbili/meron/shared/OAuthFlow.kt"
      ]
    },
    {
      "description": "Internal Task-list ordering without an established exposed native ability.",
      "paths": [
        "meron-core/src/tasks.rs"
      ]
    }
  ],
  "limitations": [
    {
      "description": "Provider handlers depend on deployment credentials and external-server behavior that source alone does not settle.",
      "paths": [
        "desktop/oauth.go",
        "mobile/shared/src/commonMain/kotlin/jp/nonbili/meron/shared/OAuthFlow.kt",
        "meron-core/src/protocol/"
      ]
    },
    {
      "description": "Native file/print adapters expose different handoff results and do not establish completion inside external applications.",
      "paths": [
        "desktop/paste_image.go",
        "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/PlatformServices.kt"
      ]
    },
    {
      "description": "Account removal suppresses core errors and mobile movement/Undo callers do not establish exact target or original-selection equivalence.",
      "paths": [
        "desktop/accounts.go",
        "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+ThreadMoves.kt"
      ]
    },
    {
      "description": "Transfer media references and platform preference mappings do not establish universal asset portability or atomic restore.",
      "paths": [
        "meron-core/src/backup.rs"
      ]
    },
    {
      "description": "Credential/key handling has platform-specific storage boundaries, including the desktop MERON_KEYRING=off branch; full local-data encryption is not established.",
      "paths": [
        "meron-core/src/"
      ]
    }
  ]
}
---

# Coverage
