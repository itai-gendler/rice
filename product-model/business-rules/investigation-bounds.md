---
appliesTo:
- type: entity
  id: meeting
- type: entity
  id: idea
- type: entity
  id: finding
references:
- kind: code
  role: implementation
  target: src/main/warroom/ipc.ts
- kind: code
  role: implementation
  target: src/main/warroom/engine.ts
- kind: code
  role: implementation
  target: src/renderer/warroom.js
---

# Ideas and investigation count cycles independently

Each track consumes its own limit: 30, 60, 120, 300 or unlimited, defaulting to 120. Extra allowance is thirty per extension. New speech is required, only one cycle runs at once and a stopped cycle can be followed by its next scheduled cycle.
