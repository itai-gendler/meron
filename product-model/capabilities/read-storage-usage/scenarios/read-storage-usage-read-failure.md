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
      "text": "Local size inspection fails.",
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
      "text": "The size error remains instead of invented successful totals.",
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

# Read storage usage — read failure

## Trigger

Local size inspection fails.

## Outcome

The size error remains instead of invented successful totals.
