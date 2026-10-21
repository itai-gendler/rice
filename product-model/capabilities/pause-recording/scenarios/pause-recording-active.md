---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Pause
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Sessions
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice pauses the meeting and releases its microphone
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Capture in use
    - Capture running
    from: Recording
    to: Paused
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
references:
- kind: code
  role: implementation
  target: src/main/session/meeting-session.ts
- kind: code
  role: implementation
  target: src/main/app/main.ts
---

# Pause a recording

## Trigger

The user chooses Pause in the meeting, tray or Mini Rice.

## Outcome

Capture stops for the pause and the meeting remains resumable.

## Edge cases

- After thirty paused minutes Rice offers Stop or Resume without stopping automatically.
