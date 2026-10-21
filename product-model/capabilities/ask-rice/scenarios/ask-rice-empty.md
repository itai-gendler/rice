---
kind: edge
routes:
  desktop: Rice desktop
steps:
- text: The user asks across meetings
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::chat
  actor: user
- text: Rice saves an all meetings chat answer explaining the empty result
  kind: product
  entities:
  - entity: all-meetings-chat
    effect: changes
    facts:
    - Turns
    - Scope
    - Citations
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

# Report no available meeting context

## Trigger

The user asks across meetings and no eligible meeting or relevant memory is found.

## Outcome

Rice returns and saves a localized no-meetings answer without an AI generation.
