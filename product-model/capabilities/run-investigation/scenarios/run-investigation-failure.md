---
kind: edge
routes:
  desktop: Rice desktop
steps:
- text: The user requests investigation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice reports the meeting cycle error
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Recording alerts
  - entity: finding
    effect: reads
    facts:
    - Text
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

# Investigation fails

## Trigger

The user requests investigation and the AI call fails or times out.

## Outcome

Rice shows the cycle error without discarding earlier findings.
