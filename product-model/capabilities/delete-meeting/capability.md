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
  target: src/main/app/delete-meeting.ts
- kind: code
  role: implementation
  target: src/main/store/drafts.ts
- kind: code
  role: implementation
  target: src/main/privacy/retention.ts
---

# Delete meeting

Move a meeting directory to the system Trash after confirmation. Empty unused drafts and expired meetings can also be discarded by Rice.
