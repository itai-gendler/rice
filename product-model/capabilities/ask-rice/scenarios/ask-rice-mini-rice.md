---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The user asks about the active meeting
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Title
  contexts:
    desktop:
      place: desktop::mini-rice
  actor: user
- text: Rice reads transcript context and prior chat
  kind: product
  entities:
  - entity: transcript
    effect: reads
    facts:
    - Content
    - Partial speech
  - entity: meeting-chat
    effect: reads
    facts:
    - Turns
  contexts:
    desktop:
      place: desktop::mini-rice
  actor: user
- text: Rice saves the meeting chat answer
  kind: product
  entities:
  - entity: meeting-chat
    effect: changes
    facts:
    - Turns
    - Answer progress
  - entity: meeting
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::mini-rice
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

# Ask from Mini Rice

## Trigger

The user opens Ask in Mini Rice while recording.

## Outcome

Rice streams and saves the answer in the same meeting chat.
