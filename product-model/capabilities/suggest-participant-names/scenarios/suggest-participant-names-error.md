---
kind: edge
routes:
  desktop: Rice desktop
steps:
- text: The user requests name suggestions
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice reports the AI failure
  kind: product
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Speaker names
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
  target: src/main/session/speaker-names.ts
---

# Name suggestion fails

## Trigger

The user asks for suggestions while the AI is unavailable.

## Outcome

Rice shows an error and preserves all existing names.
