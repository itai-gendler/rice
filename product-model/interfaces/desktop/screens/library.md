---
entities:
- entity: meeting
  shows:
  - Title
  - Date
  - Folder
- entity: folder
  shows:
  - Name
  - Parent
  - Order
  - Sensitive
  - Audio retention
  - Meeting retention
  collects:
  - Name
  - Sensitive
  - Audio retention
  - Meeting retention
references:
- kind: code
  role: implementation
  target: src/renderer/renderer.js
- kind: code
  role: implementation
  target: src/renderer/search.js
---

# Meetings and folders

The saved collection, folder hierarchy and local content search.
