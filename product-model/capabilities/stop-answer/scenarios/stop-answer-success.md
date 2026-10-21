---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Stop on the current answer
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::chat
  actor: user
- text: Rice aborts the meeting chat generation
  kind: product
  entities:
  - entity: meeting-chat
    effect: changes
    facts:
    - Answer progress
  - entity: meeting
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::chat
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
  target: src/main/app/nub-ipc.ts
---

# Stop answer

## Trigger

The user chooses Stop on the current answer.

## Outcome

Rice aborts the meeting chat generation.

## Edge cases

- All-meetings chat and Mini Rice support canceling their active answer too.
