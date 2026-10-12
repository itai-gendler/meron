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
      "text": "Request read storage usage.",
      "kind": "actor",
      "actor": "user",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::general-settings"
        },
        "android": {
          "place": "android::general-settings"
        },
        "ios": {
          "place": "ios::general-settings"
        }
      }
    },
    {
      "text": "Local database and attached-file cache size inspection succeeds.",
      "kind": "condition",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::general-settings"
        },
        "android": {
          "place": "android::general-settings"
        },
        "ios": {
          "place": "ios::general-settings"
        }
      }
    },
    {
      "text": "Calculate the attached file-cache and database byte sizes from the current storage paths. The two sizes are shown as computed results without creating a stored totals object.",
      "kind": "product",
      "entities": [],
      "contexts": {
        "desktop": {
          "place": "desktop::general-settings"
        },
        "android": {
          "place": "android::general-settings"
        },
        "ios": {
          "place": "ios::general-settings"
        }
      },
      "actor": "user"
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
  ]
}
---

# Read storage usage — primary

## Trigger

Local database and attached-file cache size inspection succeeds.

## Outcome

Calculate the attachment-cache and database byte sizes from the current storage paths. The two sizes are shown as computed results without creating a stored totals object.
