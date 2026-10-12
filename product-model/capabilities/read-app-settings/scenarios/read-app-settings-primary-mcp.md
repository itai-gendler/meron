---
{
  "kind": "primary",
  "routes": {
    "mcp": "Mcp"
  },
  "steps": [
    {
      "text": "Request read shared preferences.",
      "kind": "actor",
      "actor": "mcp-client",
      "entities": [],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      }
    },
    {
      "text": "The native preference store or published service preferences response is available.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      }
    },
    {
      "text": "Read the applicable current-platform preferences; MCP returns only its supported app-setting catalogue and redacts sensitive configuration. Applicable supported settings are readable without revealing opaque secrets.",
      "kind": "product",
      "entities": [
        {
          "entity": "app-settings",
          "effect": "reads",
          "facts": [
            "Signature"
          ]
        },
        {
          "entity": "desktop-settings",
          "effect": "reads",
          "facts": [
            "Send shortcut",
            "Conversation layout",
            "Spell check",
            "Real avatars",
            "Unread badges",
            "Unified inbox visibility",
            "Interface font",
            "Message font"
          ]
        }
      ],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      },
      "actor": "mcp-client"
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
    }
  ]
}
---

# Read app settings — primary mcp

## Trigger

The native preference store or published MCP settings response is available.

## Outcome

Read the applicable current-platform preferences; MCP returns only its supported app-setting catalogue and redacts sensitive configuration. Applicable supported settings are readable without revealing opaque secrets.
