---
appliesTo:
- type: entity
  id: idea
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

# The user curates saved ideas

The person using Rice can pin a suggestion into the meeting annotations or dismiss it from the live ideas list.
