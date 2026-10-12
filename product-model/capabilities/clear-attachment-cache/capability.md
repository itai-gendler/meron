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
      "target": "desktop/paths.go"
    },
    {
      "kind": "code",
      "role": "implementation",
      "target": "meron-core/src/protocol/media.rs"
    }
  ],
  "domain": "general"
}
---

# Clear attachment cache

After the native confirmation, remove cached attachment files and recreate the cache directory while retaining the database. The attachment cache is cleared to the achieved filesystem result; mailbox database information remains.
