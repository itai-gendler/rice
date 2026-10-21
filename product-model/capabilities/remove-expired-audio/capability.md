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
  target: src/main/privacy/retention.ts
- kind: code
  role: implementation
  target: src/main/privacy/folder-rules.ts
---

# Remove expired audio

Apply effective audio retention to completed recordings independently of whole-meeting retention. Expired audio goes to Trash.
