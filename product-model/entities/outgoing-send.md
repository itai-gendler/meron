---
{
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

# Outgoing send

States Sending, Accepted, Failed. Retry returns Failed to Sending with captured contents. Accepted means SMTP acceptance. Native optimistic records are process/UI state, not a durable outbox.

## Information kept

- **Captured contents** — The submission contents captured for the current sending attempt.
- **Origin** — The composition/conversation reference from which the attempt was captured.
- **Attempt status** — The observable sending, accepted or failed condition.
- **Failure** — The retained send failure or uncertain-outcome information.
- **Retry payload** — The captured original submission payload available to the supported retry path.

## States

### Sending

A captured attempt whose submission is in progress.

### Accepted

The SMTP submission was accepted; this is not recipient delivery.

### Failed

The attempt failed or its transport outcome remains uncertain.
