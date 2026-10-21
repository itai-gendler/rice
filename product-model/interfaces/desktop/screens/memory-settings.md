---
entities:
- entity: settings
  shows:
  - Memory enabled
  - Memory progress
  collects:
  - Memory enabled
- entity: meeting
  shows:
  - Title
references:
- kind: code
  role: implementation
  target: src/renderer/settings.js
---

# Memory settings

Whether Memory is on, and the progress of building memory from older meetings.
