---
appliesTo:
- type: entity
  id: meeting
references:
- kind: code
  role: implementation
  target: src/renderer/renderer.js
- kind: code
  role: implementation
  target: src/main/app/main.ts
- kind: code
  role: implementation
  target: src/main/app/delete-meeting.ts
- kind: code
  role: implementation
  target: src/main/privacy/retention.ts
---

# Meeting deletion and retention use the system Trash

Deleting a meeting moves its directory to Trash; retention moves expired audio or the whole meeting to Trash. Canceling confirmation leaves a manually selected meeting intact.
