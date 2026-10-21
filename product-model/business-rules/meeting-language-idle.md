---
appliesTo:
- type: entity
  id: meeting
  effect: changes
  facts:
  - Language
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
  when:
  - fact: Capture in use
    is: false
---

# Only the user changes an inactive meeting’s language

The current meeting’s language cannot be changed while its active recording session is in use.
