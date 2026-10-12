---
{
  "kind": "primary",
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
      "text": "A nonempty current composition has a supported composition destination and its save succeeds.",
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
      "text": "Append/replace supported Drafts copies identified by the stable message identity and reconcile save state. The saved Draft can be reopened; server replacement/cleanup remains subject to the actual save result.",
      "kind": "product",
      "entities": [
        {
          "entity": "draft",
          "effect": "changes",
          "facts": [
            "Stored copies",
            "Save status"
          ],
          "from": "Editing",
          "to": "Saved"
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

# Save draft — primary

## Trigger

A nonempty current composition has a supported Drafts destination and its save succeeds.

## Outcome

Append/replace supported Drafts copies identified by the stable message identity and reconcile save state. The saved Draft can be reopened; server replacement/cleanup remains subject to the actual save result.
