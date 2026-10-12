---
{
  "kind": "edge",
  "routes": {
    "desktop": "Desktop",
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request remove allowlisted address.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::trusted-senders"
        },
        "android": {
          "place": "android::trusted-senders"
        },
        "ios": {
          "place": "ios::trusted-senders"
        }
      }
    },
    {
      "text": "Persisting removal of the selected sender entry fails.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::trusted-senders"
        },
        "android": {
          "place": "android::trusted-senders"
        },
        "ios": {
          "place": "ios::trusted-senders"
        }
      }
    },
    {
      "text": "The caller reports the failure or retains the applicable prior allowlist; the requested persistent exception removal is not established.",
      "kind": "product",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::trusted-senders"
        },
        "android": {
          "place": "android::trusted-senders"
        },
        "ios": {
          "place": "ios::trusted-senders"
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


# Remove trusted sender — write failure

## Trigger

Persisting removal of the selected sender entry fails.

## Outcome

The caller reports the failure or retains the applicable prior allowlist; the requested persistent exception removal is not established.
