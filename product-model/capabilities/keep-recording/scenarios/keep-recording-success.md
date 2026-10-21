---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Keep recording on the offered notice
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice clears the meeting warning and restarts the silence wait
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Recording alerts
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

# Keep recording

## Trigger

The user chooses Keep recording on the offered notice.

## Outcome

Rice clears the meeting warning and restarts the silence wait.
