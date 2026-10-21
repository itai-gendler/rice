---
appliesTo:
- type: entity
  id: finding
  effect: changes
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
permits:
- actors:
  - user
---

# The user curates saved findings

The person using Rice can pin or unpin investigation findings, dismiss them, and bring a dismissed finding back through Undo.
