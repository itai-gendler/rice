---
kind: edge
routes:
  desktop: Rice desktop
steps:
- text: The user sends a question
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::chat
  actor: user
- text: Rice reports the meeting chat answer failure
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
  target: src/main/search/global-chat.ts
- kind: code
  role: implementation
  target: src/main/search/retrieve.ts
- kind: code
  role: implementation
  target: src/main/session/chat-context.ts
- kind: code
  role: implementation
  target: src/main/store/global-chat.ts
---

# Report an AI answer failure

## Trigger

The user sends a question and the selected AI fails.

## Outcome

Rice shows the actionable error and does not save an incomplete exchange as a completed answer.

## Edge cases

- All-meetings chat reports the same provider failure without saving a completed turn.
