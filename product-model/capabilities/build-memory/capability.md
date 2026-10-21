---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: src/main/memory/service.ts
- kind: code
  role: implementation
  target: src/main/memory/extract.ts
- kind: code
  role: implementation
  target: src/main/memory/ipc.ts
- kind: code
  role: implementation
  target: src/renderer/memory.js
domain: memory
---

# Build memory from older meetings

Start a background pass over eligible older completed meetings, one at a time, only after the user requests it.
