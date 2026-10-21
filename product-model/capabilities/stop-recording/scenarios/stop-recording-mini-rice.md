---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Stop
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
- text: Rice ends capture and starts finalizing the meeting
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Date
    - Capture in use
    - Capture running
    from: Recording
    to: Finishing
  - entity: transcript
    effect: changes
    facts:
    - Content
    - Gaps
  contexts:
    desktop:
      place: desktop::mini-rice
  actor: user
- text: Rice finishes the meeting material
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Sessions
    - Audio
    - Capture in use
    - Capture running
    from: Finishing
    to: Done
  - entity: transcript
    effect: changes
    facts:
    - Content
    - Partial speech
    - Gaps
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

# Stop recording from Mini Rice

## Trigger

The user chooses the recording control in Mini Rice.

## Outcome

The meeting is Done and its material remains available while notes may generate.
