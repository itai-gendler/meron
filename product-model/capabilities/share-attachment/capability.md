---
{
  "availability": [
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
      "target": "desktop/paste_image.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/MeronMobileState+Attachments.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/commonMain/kotlin/jp/nonbili/meron/ui/PlatformServices.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/android/src/main/java/jp/nonbili/meron/AndroidUiAdapters.kt"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "mobile/ui/src/iosMain/kotlin/jp/nonbili/meron/ui/IosMainViewController.kt"
    }
  ]
}
---

# Share attachment

Hand the available attachment file and its content type to the mobile sharing facility. The platform sharing handoff is requested without claiming a chosen recipient or completed transfer.
