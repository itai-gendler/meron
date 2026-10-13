---
{
  "kind": "configuration",
  "of": "capability-scenario",
  "settings": [
    {
      "entity": "mcp-client",
      "fact": "Delete confirmation"
    }
  ],
  "takesEffect": "When the client's request is accepted: the client's saved setting at that moment decides. A change applies to later requests.",
  "stability": "A request already pending stays pending until it is approved, denied, cancelled or expires after five minutes; it never switches to direct execution. Saving MCP settings cancels every request still pending.",
  "alternatives": [
    {
      "id": "empty-folder-agent-pending",
      "selectedWhen": "Delete confirmation is Ask every time. This is the default, and a missing value means ask."
    },
    {
      "id": "empty-folder-agent-direct",
      "selectedWhen": "Delete confirmation is Allow without asking. It can be set only while the client has the Delete grant."
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp.go"
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
      "target": "desktop/frontend/src/components/dialog/McpSettingsPanel.tsx"
    }
  ]
}
---

# Agent empty Trash confirmation

Emptying Trash for an agent follows the same per-client deletion setting as permanent delete: ask first, or empty without asking. Both forms are supported, and the setting on the requesting client decides which applies.
