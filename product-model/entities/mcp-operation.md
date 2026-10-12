---
{
  "domain": "mcp-access",
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_tools.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_configuration.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_mutations.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/mcp_operations.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/mcp_mail.rs"
    }
  ]
}
---


# MCP operation

States Pending approval, Running, Completed, Failed, Denied, Cancelled, Expired. Pending/direct execution, denial, invalidation and checked expiry produce these states; records are retained in process memory.

## Information kept

- **Requesting client** — The connection captured when the request is created.
- **Action** — The requested sending or permanent-deletion operation.
- **Account** — The account targeted by the retained request.
- **Request identity** — The client request identity used during bounded idempotency retention.
- **Argument fingerprint** — The retained fingerprint of the requested tool and arguments.
- **Preview** — The content/selection shown for a pending request.
- **Approved selection** — The captured contents or exact deletion snapshot used by execution.
- **Expiry** — The time after which a pending request expires when checked.
- **Result** — The completed result returned for the retained operation.
- **Error** — The execution failure returned for this retained operation.

## States

### Pending approval

A captured operation waiting for review, or the initial state before configured direct execution.

### Running

A captured operation is executing.

### Completed

The frozen action completed successfully; a send result means SMTP acceptance.

### Failed

The frozen action returned an execution error; a failed send can still have an uncertain transport outcome.

### Denied

The local review denied the pending action without executing it.

### Cancelled

A pending operation closed after configuration or access invalidation.

### Expired

A pending operation whose five-minute expiry was reached when checked.
