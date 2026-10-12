---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "mail-account",
      "effect": "changes",
      "facts": [
        "Display name",
        "Sender name",
        "Signature",
        "Load remote images",
        "Conversation HTML",
        "Unified inclusion",
        "Muted",
        "Paused",
        "Save sent copy"
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
          "fact": "Manage accounts grant",
          "is": true
        }
      ]
    }
  ]
}
---

# Account managers change supported mail preferences

The account allowlist controls only display_name, sender_name, aliases, signature, load_remote_images, conversation_html, included_in_unified, muted, paused and save_sent_copy; aliases have their own effect rules.
