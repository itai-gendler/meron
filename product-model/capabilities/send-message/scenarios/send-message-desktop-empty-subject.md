---
{
  "kind": "validation",
  "routes": {
    "desktop": "Desktop"
  },
  "steps": [
    {
      "text": "Request send message.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::composer"
        }
      }
    },
    {
      "text": "The empty-subject warning is declined.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::composer"
        }
      }
    },
    {
      "text": "No transport attempt is submitted; accepting the warning follows the ordinary send path.",
      "kind": "product",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::composer"
        }
      },
      "actor": "user"
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

# Send message — desktop empty subject

## Trigger

The empty-subject warning is declined.

## Outcome

No transport attempt is submitted; accepting the warning follows the ordinary send path.
