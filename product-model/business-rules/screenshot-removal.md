---
appliesTo:
- type: entity
  id: screenshot
  effect: removes
references:
- kind: code
  role: implementation
  target: src/main/screenshots/ipc.ts
- kind: code
  role: implementation
  target: src/main/screenshots/store.ts
permits:
- actors:
  - user
---

# The user removes saved screenshots

The person using Rice can remove a saved capture from its meeting.
