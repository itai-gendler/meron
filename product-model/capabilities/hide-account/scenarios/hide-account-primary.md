---
{
  "kind": "primary",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request hide account.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        }
      }
    },
    {
      "text": "The selected account is visible and Hide is chosen.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        }
      }
    },
    {
      "text": "Add the selected account to the hidden side-navigation selections. The account is hidden from navigation; its data remains and its settings toggle can restore visibility.",
      "kind": "product",
      "entities": [
        {
          "entity": "desktop-settings",
          "effect": "changes",
          "facts": [
            "Hidden accounts"
          ]
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::mailbox"
        }
      },
      "actor": "user"
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
    }
  ]
}
---

# Hide account — primary

## Trigger

The selected account is visible and Hide is chosen.

## Outcome

Add the selected account to the hidden side-navigation selections. The account is hidden from navigation; its data remains and its settings toggle can restore visibility.
