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
      "text": "Request save composition.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::composer"
        },
        "android": {
          "place": "android::composer"
        },
        "ios": {
          "place": "ios::composer"
        }
      }
    },
    {
      "text": "The applicable save fails.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::composer"
        },
        "android": {
          "place": "android::composer"
        },
        "ios": {
          "place": "ios::composer"
        }
      }
    },
    {
      "text": "Retain the editable draft and report its failed save status without claiming a successfully stored replacement.",
      "kind": "product",
      "entities": [
        {
          "entity": "draft",
          "effect": "changes",
          "facts": [
            "Save status"
          ]
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::composer"
        },
        "android": {
          "place": "android::composer"
        },
        "ios": {
          "place": "ios::composer"
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


# Save draft — save failure

## Trigger

The applicable save fails.

## Outcome

The editable composition remains available with its failed save status. Prior server copies can remain; a failed append or later replacement cleanup does not establish a successful new server copy or rollback of earlier work.
