---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: Rice opens and finds a meeting left in Finishing.
  kind: condition
  entities:
  - entity: meeting
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  unattended: true
- text: Rice marks it Interrupted and offers recovery.
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Capture in use
    - Capture running
    from: Finishing
    to: Interrupted
  contexts:
    desktop:
      place: desktop::meeting
references:
- kind: code
  role: implementation
  target: src/renderer/renderer.js
- kind: code
  role: implementation
  target: src/main/app/main.ts
- kind: code
  role: implementation
  target: src/main/session/recovery.ts
- kind: code
  role: implementation
  target: src/main/session/recover-meeting.ts
---

# Recognize interrupted finalization

## Trigger

Rice opens and finds a meeting left in Finishing.

## Outcome

Rice marks it Interrupted and offers recovery.
