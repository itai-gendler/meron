---
{
  "availability": [
    {
      "place": "desktop"
    },
    {
      "place": "android"
    },
    {
      "place": "ios"
    }
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/accounts.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/frontend/src/components/dialog/useAccountDialog.ts#useAccountDialog"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Accounts.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/protocol/accounts.rs#add_mobile_password_account"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/store/accounts.rs"
    }
  ],
  "domain": "mail-accounts"
}
---

# Trust mail certificate

Probe the relevant IMAP/SMTP endpoint, present its fingerprint, retain the user-accepted protocol-specific pin, and retry the supported failed attempt. The accepted trust choice is retained for that endpoint/protocol; another changed or rejected certificate can require a new prompt.
