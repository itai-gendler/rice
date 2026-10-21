---
appliesTo:
- type: entity
  id: notes
- type: entity
  id: annotations
references:
- kind: code
  role: implementation
  target: src/main/session/notes.ts#keepAnnotations
---

# Generated notes preserve the person’s annotations

User jottings guide the chosen sections. Any annotation the AI did not incorporate is appended to Other notes, preserving its text.
