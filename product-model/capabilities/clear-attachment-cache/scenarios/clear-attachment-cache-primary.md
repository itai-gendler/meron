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
      "text": "The local attached-file cache is selected for clearing and file removal succeeds.",
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
      "text": "After the native confirmation, remove cached attachment files and recreate the cache directory while retaining the database. The attachment cache is cleared to the achieved filesystem result; mailbox database information remains.",
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

# Clear attachment cache — primary

## Trigger

The local attached-file cache is selected for clearing and file removal succeeds.

## Outcome

After the native confirmation, remove cached attachment files and recreate the cache directory while retaining the database. The attachment cache is cleared to the achieved filesystem result; mailbox database information remains.
