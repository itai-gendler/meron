---
{
  "kind": "edge",
  "routes": {
    "desktop": "Desktop",
    "android": "Android",
    "ios": "Ios"
  },
  "steps": [
    {
      "text": "Request clear attached file cache.",
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
      "text": "Some cached files cannot be removed.",
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
      "text": "Deleted cache files remain deleted; remaining files and database are retained.",
      "kind": "product",
      "entities": [
        {
          "entity": "attachment",
          "effect": "changes",
          "facts": [
            "Content availability",
            "Content location"
          ]
        }
      ],
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

# Clear attachment cache — clear failure

## Trigger

Some cached files cannot be removed.

## Outcome

Deleted cache files remain deleted; remaining files and database are retained.
