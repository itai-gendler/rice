---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The computer wakes after sleeping during a recording.
  kind: condition
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  unattended: true
- text: Rice restarts capture on the existing timeline and shows the sleep gap.
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Recording alerts
  - entity: transcript
    effect: changes
    facts:
    - Content
    - Gaps
  contexts:
    desktop:
      place: desktop::meeting
references:
- kind: code
  role: implementation
  target: src/main/session/meeting-session.ts
- kind: code
  role: implementation
  target: src/main/app/main.ts
- kind: code
  role: implementation
  target: src/main/app/record-shortcut.ts
- kind: code
  role: implementation
  target: src/main/session/prompt-policy.ts
---

# Resume after computer sleep

## Trigger

The computer wakes after sleeping during a recording.

## Outcome

Rice restarts capture on the existing timeline and shows the sleep gap.

## Edge cases

- A manually paused meeting remains paused when the computer wakes.
