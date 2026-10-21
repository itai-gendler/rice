---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Resume
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice resumes the meeting and records the pause in the transcript
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Capture in use
    - Capture running
    from: Paused
    to: Recording
  - entity: transcript
    effect: changes
    facts:
    - Content
    - Gaps
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

# Resume recording

## Trigger

The user chooses Resume.

## Outcome

Rice resumes the meeting and records the pause in the transcript.
