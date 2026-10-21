---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses a microphone for the active meeting
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice switches capture and records the meeting microphone change
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Microphone
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
  target: src/renderer/mic-chip.js
- kind: code
  role: implementation
  target: src/main/platform/mic-pick.ts
---

# Switch microphone

## Trigger

The user chooses a microphone for the active meeting.

## Outcome

Rice switches capture and records the meeting microphone change.
