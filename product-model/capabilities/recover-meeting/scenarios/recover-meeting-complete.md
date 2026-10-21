---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user asks Rice to recover the meeting
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
- text: Rice transcribes uncovered audio and finalizes the meeting
  kind: product
  entities:
  - entity: transcript
    effect: changes
    facts:
    - Content
  - entity: meeting
    effect: changes
    facts:
    - Audio
    - Date
    - Sessions
    - Capture in use
    - Capture running
    from: Interrupted
    to: Done
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
  target: src/main/session/recovery.ts
- kind: code
  role: implementation
  target: src/main/session/recover-meeting.ts
---

# Recover interrupted material

## Trigger

The user chooses Recover meeting.

## Outcome

The meeting becomes Done with recovered material and notes requested when text exists.

## Edge cases

- Failure is reported and the existing meeting material remains available.
- The user can choose Continue recording instead.
