---
{
  "appliesTo": [
    {
      "type": "entity",
      "id": "mcp-operation",
      "effect": "creates",
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
      "related": [
        {
          "verb": "is targeted by",
          "entity": "mail-account"
        },
        {
          "verb": "has explicit access to",
          "entity": "mcp-client"
        }
      ],
      "when": [
        {
          "entity": "mcp-settings",
          "fact": "Enabled",
          "is": true
        },
        {
          "entity": "mcp-client",
          "fact": "Send grant",
          "is": true
        },
        {
          "fact": "Action",
          "is": "send_message"
        }
      ]
    },
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
          "fact": "Send grant",
          "is": true
        },
        {
          "entity": "mcp-client",
          "fact": "All accounts",
          "is": true
        },
        {
          "fact": "Action",
          "is": "send_message"
        }
      ]
    },
    {
      "related": [
        {
          "verb": "is targeted by",
          "entity": "mail-account"
        },
        {
          "verb": "has explicit access to",
          "entity": "mcp-client"
        }
      ],
      "when": [
        {
          "entity": "mcp-settings",
          "fact": "Enabled",
          "is": true
        },
        {
          "entity": "mcp-client",
          "fact": "Delete grant",
          "is": true
        },
        {
          "fact": "Action",
          "is": "delete_permanently"
        }
      ]
    },
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
          "fact": "Delete grant",
          "is": true
        },
        {
          "entity": "mcp-client",
          "fact": "All accounts",
          "is": true
        },
        {
          "fact": "Action",
          "is": "delete_permanently"
        }
      ]
    },
    {
      "related": [
        {
          "verb": "is targeted by",
          "entity": "mail-account"
        },
        {
          "verb": "has explicit access to",
          "entity": "mcp-client"
        }
      ],
      "when": [
        {
          "entity": "mcp-settings",
          "fact": "Enabled",
          "is": true
        },
        {
          "entity": "mcp-client",
          "fact": "Delete grant",
          "is": true
        },
        {
          "fact": "Action",
          "is": "empty_trash"
        }
      ]
    },
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
          "fact": "Delete grant",
          "is": true
        },
        {
          "entity": "mcp-client",
          "fact": "All accounts",
          "is": true
        },
        {
          "fact": "Action",
          "is": "empty_trash"
        }
      ]
    }
  ]
}
---

# Scoped clients with the action grant create retained requests

Account scope and the action’s Send or Delete grant admit retained operation creation; enabled service, current bearer binding, valid frozen inputs, capacity and idempotency checks also apply.
