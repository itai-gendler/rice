---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Stop during a cycle
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice cancels the active meeting cycle and clears its running progress
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

# Stop investigation cycle

## Trigger

The user chooses Stop during a cycle.

## Outcome

Rice cancels the active meeting cycle and clears its running progress.
