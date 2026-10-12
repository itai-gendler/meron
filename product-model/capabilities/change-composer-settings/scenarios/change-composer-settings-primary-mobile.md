---
{
  "kind": "primary",
  "routes": {
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request change composer settings.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::composer-settings"
        },
        "ios": {
          "place": "ios::composer-settings"
        }
      }
    },
    {
      "text": "The applicable signature/composition values match supported types and signature limits.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::composer-settings"
        },
        "ios": {
          "place": "ios::composer-settings"
        }
      }
    },
    {
      "text": "Apply the selected native Composer preference or shared signature; MCP accepts only signature, send shortcut and spell-check keys. The selected supported composition choice is retained without asserting a shared rich-editor contract.",
      "kind": "product",
      "entities": [
        {
          "entity": "app-settings",
          "effect": "changes",
          "facts": [
            "Signature"
          ]
        },
        {
          "entity": "mobile-settings",
          "effect": "changes",
          "facts": [
            "Composition preferences"
          ]
        }
      ],
      "contexts": {
        "android": {
          "place": "android::composer-settings"
        },
        "ios": {
          "place": "ios::composer-settings"
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

# Change composer settings — primary mobile

## Trigger

The applicable signature/composition values match supported types and signature limits.

## Outcome

Apply the selected native Composer preference or shared signature; MCP accepts only signature, send shortcut and spell-check keys. The selected supported composition choice is retained without asserting a shared rich-editor contract.
