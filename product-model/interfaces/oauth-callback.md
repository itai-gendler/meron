---
{
  "type": "webhook",
  "actors": [
    "identity-provider"
  ],
  "languages": [
    "en"
  ],
  "references": [
    {
      "kind": "code",
      "role": "implementation",
      "target": "desktop/oauth.go#serveOAuthRedirect"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/shared/src/commonMain/kotlin/jp/nonbili/meron/shared/OAuthFlow.kt#parseOAuthCallbackUrlForRedirect"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+OAuth.kt"
    }
  ]
}
---

# OAuth callback

The inbound authentication result for a pending account flow, delivered through desktop loopback or supported mobile redirects. State, redirect and code checks validate the flow before exchange.
