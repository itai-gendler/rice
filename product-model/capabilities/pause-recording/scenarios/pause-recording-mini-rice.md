---
kind: alternate
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
      place: desktop::mini-rice
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
      place: desktop::mini-rice
  actor: user
references:
- kind: code
  role: implementation
  target: src/main/session/meeting-session.ts
- kind: code
  role: implementation
  target: src/main/app/main.ts
---

# Pause recording from Mini Rice

## Trigger

The user chooses the recording control in Mini Rice.

## Outcome

Capture stops for the pause and the meeting remains resumable.
