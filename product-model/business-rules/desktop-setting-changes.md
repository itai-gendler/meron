---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "desktop-settings",
      "effect": "changes",
      "facts": [
        "Send shortcut",
        "Conversation layout",
        "Spell check",
        "Real avatars",
        "Unread badges",
        "Unified inbox visibility",
        "Interface font",
        "Message font"
      ],
      "contexts": [
        {
          "place": "mcp"
        }
      ]
    }
  ],
  "references": [
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
      "target": "desktop/mcp_operations.go"
    }
  ],
  "permits": [
    {
      "actors": [
        "mcp-client"
      ],
      "when": [
        {
          "entity": "mcp-settings",
          "fact": "Enabled",
          "is": true
        },
        {
          "entity": "mcp-client",
          "fact": "Manage settings grant",
          "is": true
        }
      ]
    }
  ]
}
---

# Settings managers change supported desktop preferences

The allowlist is send_shortcut, conversation_layout, spell_check, show_real_avatars, show_unread_account_badge, show_unified_inbox_in_sidenav, font_family and message_font_family; supported signature is governed separately.
