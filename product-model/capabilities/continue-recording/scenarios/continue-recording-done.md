---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Continue recording
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Title
    - Sessions
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice starts another stretch and preserves existing material
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Sessions
    - Microphone
    - Audio
    - Capture in use
    - Capture running
    from: Done
    to: Recording
  - entity: transcript
    effect: changes
    facts:
    - Content
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

# Continue a done meeting

## Trigger

The user chooses Continue recording.

## Outcome

New speech and audio append to the same meeting; stopping regenerates notes from the accumulated transcript.
