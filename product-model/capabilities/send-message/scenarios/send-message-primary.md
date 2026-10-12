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
      "text": "Request send message.",
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
      "text": "The composition has valid recipients and supported content; native subject validation or its warning is satisfied and SMTP accepts the submission.",
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
      "text": "Begin the captured SMTP attempt.",
      "kind": "product",
      "entities": [
        {
          "entity": "outgoing-send",
          "effect": "creates",
          "facts": [
            "Captured contents",
            "Origin",
            "Attempt status",
            "Failure",
            "Retry payload"
          ],
          "to": "Sending"
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
    },
    {
      "text": "Capture the exact selected native composition and dispatch SMTP using the configured account/identity, recipients, contents and attached file. A captured sending attempt is visible; on SMTP acceptance it becomes Accepted, then Sent-copy work and consumed-composition cleanup continue separately.",
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
          "place": "android::composer"
        },
        "ios": {
          "place": "ios::composer"
        }
      },
      "actor": "user"
    },
    {
      "text": "When the configured Sent-copy path applies and succeeds, retain its stored copy; remove only successfully cleaned consumed stored compositions, preserving a newer reply using the same identity.",
      "kind": "product",
      "entities": [
        {
          "entity": "email-message",
          "effect": "creates",
          "facts": [
            "Location",
            "Message identity",
            "Sender",
            "Recipients",
            "Reply information",
            "Subject",
            "Date",
            "Plain content",
            "HTML content",
            "Thread information",
            "Unread",
            "Starred",
            "Body availability"
          ]
        },
        {
          "entity": "draft",
          "effect": "removes",
          "from": "Saved"
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


# Send message — primary

## Trigger

The composition has valid recipients and supported content; native subject validation or its warning is satisfied and SMTP accepts the submission.

## Outcome

Capture the exact selected native composition and dispatch SMTP using the configured account/identity, recipients, contents and attachments. A captured sending attempt is visible; on SMTP acceptance it becomes Accepted, then Sent-copy work and consumed-draft cleanup continue separately.

## Decision points

### Sent copy

Does the account’s Save sent copy choice require a separate copy?

- The configured/provider-default path requires a copy and succeeds → the Sent copy is retained after acceptance.
- The copy is disabled or the provider path does not need one → no separate Sent-copy creation is asserted; the submission remains accepted.

### Consumed composition

Is there an applicable consumed server Draft copy that is no longer used by a newer reply?

- Applicable copies exist and cleanup succeeds → those copies are removed without resurrecting the consumed buffer.
- No applicable stored copy exists, or a newer reply still owns it → no stored-copy removal is asserted; the accepted send remains independent of that composition.
