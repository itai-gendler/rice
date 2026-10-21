---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The investigation interval is due during unpaused recording in an active War room.
  kind: condition
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Mode
    - Investigation settings
    - Extra cycles
  contexts:
    desktop:
      place: desktop::meeting
  unattended: true
- text: Rice adds findings and updates the meeting investigation count.
  kind: product
  entities:
  - entity: finding
    effect: creates
    facts:
    - Text
    - Time
    - Source
    - Pinned
    to: Visible
  - entity: meeting
    effect: changes
    facts:
    - Investigation count
  - entity: transcript
    effect: reads
    facts:
    - Content
  contexts:
    desktop:
      place: desktop::meeting
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

# Run a scheduled investigation

## Trigger

The investigation interval is due during unpaused recording in an active War room.

## Outcome

Rice adds findings and updates the meeting investigation count.
