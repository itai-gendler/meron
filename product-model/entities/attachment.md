---
{
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

# Attachment

Independently addressed cached/attached content can be read, opened, saved/shared or cleared locally. Host handoff does not necessarily mean durable saving.

## Information kept

- **Filename** — The original or configured attachment filename.
- **Media type** — The attachment content type.
- **Size** — The declared or obtained byte size.
- **Content availability** — Whether usable attachment bytes are present locally.
- **Content location** — The supported cache key/local reference from which bytes can be obtained.
- **Inline identity** — The inline attachment/content identity when present.
