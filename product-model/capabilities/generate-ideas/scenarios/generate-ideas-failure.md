---
kind: edge
routes:
  desktop: Rice desktop
steps:
- text: The user requests ideas now
  kind: actor
  entities:
  - entity: idea
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice reports the meeting cycle failure
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Recording alerts
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
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

# Idea generation fails

## Trigger

The user requests ideas but the AI times out or returns unusable content.

## Outcome

Rice shows the cycle error and waits for the next scheduled cycle or a manual retry.
