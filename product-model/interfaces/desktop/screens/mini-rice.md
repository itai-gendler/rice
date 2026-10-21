---
entities:
- entity: meeting
  shows:
  - Title
  - Sessions
  - Recording alerts
- entity: transcript
  shows:
  - Content
  - Partial speech
- entity: meeting-chat
  shows:
  - Turns
  - Answer progress
references:
- kind: code
  role: implementation
  target: src/renderer/nub.js
- kind: code
  role: implementation
  target: src/main/app/nub-ipc.ts
---

# Mini Rice

The active recording and its compact meeting chat.
