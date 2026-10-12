---
{
  "kind": "primary",
  "result": "achieved",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Open the supported mailto URI.",
      "kind": "actor",
      "actor": "user",
      "capability": "create-draft",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        }
      }
    },
    {
      "text": "Create the draft with the supported URI recipients, subject and body.",
      "kind": "product",
      "actor": "user",
      "capability": "create-draft",
      "entities": [
        {
          "entity": "draft",
          "effect": "creates",
          "facts": [
            "Sending identity",
            "Recipients",
            "Subject",
            "Plain content",
            "HTML content",
            "Reply information",
            "Message identity",
            "Stored copies",
            "Save status"
          ],
          "to": "Editing"
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        }
      }
    },
    {
      "text": "Open the full composer with the prepared contents.",
      "kind": "product",
      "actor": "user",
      "capability": "create-draft",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::composer"
        }
      }
    },
    {
      "text": "Edit the recipients, subject or composition contents.",
      "kind": "actor",
      "actor": "user",
      "capability": "edit-draft",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::composer"
        }
      }
    },
    {
      "text": "Retain the edited draft fields without submitting SMTP.",
      "kind": "product",
      "actor": "user",
      "capability": "edit-draft",
      "entities": [
        {
          "entity": "draft",
          "effect": "changes",
          "facts": [
            "Sending identity",
            "Recipients",
            "Subject",
            "Plain content",
            "HTML content",
            "Reply information"
          ]
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::composer"
        }
      }
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/compose.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/quickReplySend.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/states/pendingSends.ts"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Compose.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+QuickReply.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/sidecar/dispatch/compose.rs"
    }
  ]
}
---


# Edit the composition opened by creation — mailto

## Trigger

Desktop receives a supported mailto URI.

## Outcome

The Product opens the supported full editor with the prepared composition and the person edits it.
