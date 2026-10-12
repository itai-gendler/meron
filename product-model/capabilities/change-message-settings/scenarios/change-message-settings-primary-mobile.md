---
{
  "kind": "primary",
  "routes": {
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request change message settings.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::messages-settings"
        },
        "ios": {
          "place": "ios::messages-settings"
        }
      }
    },
    {
      "text": "The applicable message-presentation values match supported conversation/font preference types.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "android": {
          "place": "android::messages-settings"
        },
        "ios": {
          "place": "ios::messages-settings"
        }
      }
    },
    {
      "text": "Apply the selected Messages preference to the current platform; MCP supports conversation layout/message font on desktop only. The selected platform retains its supported Messages choice.",
      "kind": "product",
      "entities": [
        {
          "entity": "mobile-settings",
          "effect": "changes",
          "facts": [
            "Conversation layout"
          ]
        }
      ],
      "contexts": {
        "android": {
          "place": "android::messages-settings"
        },
        "ios": {
          "place": "ios::messages-settings"
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

# Change message settings — primary mobile

## Trigger

The applicable message-presentation values match supported conversation/font preference types.

## Outcome

Apply the selected Messages preference to the current platform; MCP supports conversation layout/message font on desktop only. The selected platform retains its supported Messages choice.
