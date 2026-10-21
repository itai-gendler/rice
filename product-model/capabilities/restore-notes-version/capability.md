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
  target: src/main/store/notes-versions.ts#restoreVersion
---

# Restore notes version

Make selected historical notes current and retain the replaced current notes in history.
