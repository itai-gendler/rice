---
appliesTo:
- type: entity
  id: meeting
  effect: changes
references:
- kind: code
  role: implementation
  target: src/renderer/renderer.js
- kind: code
  role: implementation
  target: src/main/app/main.ts
permits:
- actors:
  - user
- unattended: true
---

# The user manages meetings and Rice updates recording progress

The person using Rice manages meeting preferences and recording. Rice updates the same meeting as capture, finalization, repair detection and enabled background cycles progress. Language changes have their own active-session condition.
