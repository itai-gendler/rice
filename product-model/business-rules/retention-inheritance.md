---
appliesTo:
- type: entity
  id: folder
- type: entity
  id: meeting
- type: entity
  id: settings
  facts:
  - Default retention
references:
- kind: code
  role: implementation
  target: src/main/privacy/folder-rules.ts
- kind: code
  role: implementation
  target: src/main/privacy/retention.ts
- kind: code
  role: implementation
  target: src/main/store/folders.ts
---

# Audio and meeting retention inherit independently

Each value comes from the nearest folder specifying that value, then the global default. Keep forever explicitly overrides inheritance. Audio offers forever, 7, 30 or 90 days; whole meetings offer forever, 6 or 12 months.
