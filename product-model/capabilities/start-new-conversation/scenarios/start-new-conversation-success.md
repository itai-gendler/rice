---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses New conversation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::chat
  actor: user
- text: Rice clears the active all meetings chat context
  kind: product
  entities:
  - entity: all-meetings-chat
    effect: changes
    facts:
    - Turns
    - Citations
    - Web sources
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
  target: src/main/store/global-chat.ts#startNewGlobalConversation
---

# Start new conversation

## Trigger

The user chooses New conversation.

## Outcome

Rice clears the active all meetings chat context.

## Edge cases

- Earlier turns remain in the local history file; the active conversation reads only turns after the reset.
- Resetting an already empty conversation has no effect.
