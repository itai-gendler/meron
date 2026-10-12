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

# Copy image

Invoke Copy image with available image bytes: desktop uses clipboard support, while Android/iOS adapters invoke sharing. The platform-specific copy/share handoff completes to the reported host boundary.
