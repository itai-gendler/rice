---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: src/renderer/renderer.js
- kind: code
  role: implementation
  target: src/main/app/main.ts
- kind: code
  role: implementation
  target: src/main/session/recovery.ts
- kind: code
  role: implementation
  target: src/main/session/recover-meeting.ts
---

# Recover meeting

Finish interrupted audio, transcribe its uncovered tail locally and generate notes when speech exists.
