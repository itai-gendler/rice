---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user edits annotations
  kind: actor
  entities:
  - entity: annotations
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice saves annotations and their line times
  kind: product
  entities:
  - entity: annotations
    effect: changes
    facts:
    - Text
    - Times
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
references:
- kind: code
  role: implementation
  target: src/renderer/renderer.js
- kind: code
  role: implementation
  target: src/main/app/main.ts
- kind: code
  role: implementation
  target: src/main/store/annotations.ts
---

# Edit annotations

## Trigger

The user edits annotations.

## Outcome

Rice saves annotations and their line times.
