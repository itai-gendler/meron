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
      "text": "Request retry send.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::composer"
        },
        "android": {
          "place": "android::conversation"
        },
        "ios": {
          "place": "ios::conversation"
        }
      }
    },
    {
      "text": "A failed native send retains its captured retry contents and the supported retry succeeds; mobile uses quick reply.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::composer"
        },
        "android": {
          "place": "android::conversation"
        },
        "ios": {
          "place": "ios::conversation"
        }
      }
    },
    {
      "text": "Begin the captured SMTP attempt.",
      "kind": "product",
      "entities": [
        {
          "entity": "outgoing-send",
          "effect": "changes",
          "facts": [
            "Attempt status",
            "Failure",
            "Retry payload"
          ],
          "from": "Failed",
          "to": "Sending"
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::composer"
        },
        "android": {
          "place": "android::conversation"
        },
        "ios": {
          "place": "ios::conversation"
        }
      },
      "actor": "user"
    },
    {
      "text": "Retry the retained original submission payload, including retained attached file bytes on desktop; mobile retries its captured quick-reply payload. The failed attempt returns to Sending with captured content, rather than replacing it with later editor changes.",
      "kind": "product",
      "entities": [
        {
          "entity": "outgoing-send",
          "effect": "changes",
          "facts": [
            "Attempt status",
            "Failure"
          ],
          "from": "Sending",
          "to": "Accepted"
        }
      ],
      "contexts": {
        "desktop": {
          "place": "desktop::composer"
        },
        "android": {
          "place": "android::conversation"
        },
        "ios": {
          "place": "ios::conversation"
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


# Retry send — primary

## Trigger

A failed native send retains its captured retry contents and the supported retry succeeds; mobile uses quick reply.

## Outcome

The retry submits the original captured contents through the supported native route and becomes Accepted when SMTP accepts them. It does not replace that payload with later editor changes or establish recipient delivery. Mobile exposes this retry for the captured quick reply.
