---
{
  "acts": "external",
  "kind": "system",
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

# Identity provider

Google or Microsoft returns an authentication result for the pending OAuth account-connection flow.
