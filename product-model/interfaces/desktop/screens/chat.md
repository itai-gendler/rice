---
entities:
- entity: meeting
  shows:
  - Title
- entity: meeting-chat
  shows:
  - Turns
  - Web sources
  - Answer progress
  - Web search
- entity: all-meetings-chat
  shows:
  - Turns
  - Scope
  - Citations
  - Web sources
  - Answer progress
  - Web search
- entity: saved-question
  shows:
  - Text
  collects:
  - Text
- entity: settings
  shows:
  - AI provider
  - AI model
references:
- kind: code
  role: implementation
  target: src/renderer/global-chat.js
- kind: code
  role: implementation
  target: src/renderer/renderer.js
---

# Ask Rice

A conversation about one meeting, all meetings or a folder, with source links.
