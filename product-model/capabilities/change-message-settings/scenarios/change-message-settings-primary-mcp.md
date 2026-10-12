---
{
  "kind": "primary",
  "routes": {
    "mcp": "Mcp"
  },
  "steps": [
    {
      "text": "Request the supported preference changes individually through their published setting calls.",
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
      "text": "Each listed preference has a valid supplied value and each independent one-key write succeeds.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      }
    },
    {
      "text": "Persist the supplied conversation_layout setting value for its configured target.",
      "kind": "product",
      "actor": "mcp-client",
      "entities": [
        {
          "entity": "desktop-settings",
          "effect": "changes",
          "facts": [
            "Conversation layout"
          ]
        }
      ],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      }
    },
    {
      "text": "Persist the supplied message_font_family setting value for its configured target.",
      "kind": "product",
      "actor": "mcp-client",
      "entities": [
        {
          "entity": "desktop-settings",
          "effect": "changes",
          "facts": [
            "Message font"
          ]
        }
      ],
      "contexts": {
        "mcp": {
          "place": "mcp"
        }
      }
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


# Change message settings — primary mcp

## Trigger

Each listed preference has a valid supplied value and each independent one-key write succeeds.

## Outcome

Each individually supplied supported preference is saved and its configuration-change result is returned. Each request changes one published key; these calls are not an atomic multi-field patch.
