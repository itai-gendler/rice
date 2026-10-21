---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user changes web search for the conversation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::chat
  actor: user
- text: Rice remembers the meeting chat web search choice for the conversation
  kind: product
  entities:
  - entity: meeting-chat
    effect: changes
    facts:
    - Web search
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
  target: src/renderer/web-search.js
- kind: code
  role: implementation
  target: src/main/ai/web-search.ts
---

# Change chat settings

## Trigger

The user changes web search for the conversation.

## Outcome

Rice remembers the meeting chat web search choice for the conversation.

## Edge cases

- All-meetings chat keeps its own search choice.
