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
      "text": "Persist the supplied display_name setting value for its configured target.",
      "kind": "product",
      "actor": "mcp-client",
      "entities": [
        {
          "entity": "mail-account",
          "effect": "changes",
          "facts": [
            "Display name"
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
      "text": "Persist the supplied sender_name setting value for its configured target.",
      "kind": "product",
      "actor": "mcp-client",
      "entities": [
        {
          "entity": "mail-account",
          "effect": "changes",
          "facts": [
            "Sender name"
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
      "text": "Persist the supplied signature setting value for its configured target.",
      "kind": "product",
      "actor": "mcp-client",
      "entities": [
        {
          "entity": "mail-account",
          "effect": "changes",
          "facts": [
            "Signature"
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
      "text": "Persist the supplied load_remote_images setting value for its configured target.",
      "kind": "product",
      "actor": "mcp-client",
      "entities": [
        {
          "entity": "mail-account",
          "effect": "changes",
          "facts": [
            "Load remote images"
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
      "text": "Persist the supplied conversation_html setting value for its configured target.",
      "kind": "product",
      "actor": "mcp-client",
      "entities": [
        {
          "entity": "mail-account",
          "effect": "changes",
          "facts": [
            "Conversation HTML"
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
      "text": "Persist the supplied included_in_unified setting value for its configured target.",
      "kind": "product",
      "actor": "mcp-client",
      "entities": [
        {
          "entity": "mail-account",
          "effect": "changes",
          "facts": [
            "Unified inclusion"
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
      "text": "Persist the supplied muted setting value for its configured target.",
      "kind": "product",
      "actor": "mcp-client",
      "entities": [
        {
          "entity": "mail-account",
          "effect": "changes",
          "facts": [
            "Muted"
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
      "text": "Persist the supplied paused setting value for its configured target.",
      "kind": "product",
      "actor": "mcp-client",
      "entities": [
        {
          "entity": "mail-account",
          "effect": "changes",
          "facts": [
            "Paused"
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
      "text": "Persist the supplied save_sent_copy setting value for its configured target.",
      "kind": "product",
      "actor": "mcp-client",
      "entities": [
        {
          "entity": "mail-account",
          "effect": "changes",
          "facts": [
            "Save sent copy"
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


# Change mail account settings — primary mcp

## Trigger

Each listed preference has a valid supplied value and each independent one-key write succeeds.

## Outcome

Each individually supplied supported preference is saved and its configuration-change result is returned. Each request changes one published key; these calls are not an atomic multi-field patch.
