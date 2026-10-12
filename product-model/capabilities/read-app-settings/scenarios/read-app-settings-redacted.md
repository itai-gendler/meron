---
{
  "kind": "alternative",
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
      "text": "The supported MCP preference read is requested.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      }
    },
    {
      "text": "Only allowed app fields are returned, omitting proxy credentials, arbitrary preferences and platform-only settings.",
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

# Read app settings — redacted

## Trigger

The supported MCP preference read is requested.

## Outcome

Only allowed app fields are returned, omitting proxy credentials, arbitrary preferences and platform-only settings.
