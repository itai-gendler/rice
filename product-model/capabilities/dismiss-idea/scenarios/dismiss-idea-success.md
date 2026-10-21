---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user dismisses an idea
  kind: actor
  entities:
  - entity: idea
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice marks the idea dismissed
  kind: product
  entities:
  - entity: idea
    effect: changes
    facts: []
    from: Suggested
    to: Dismissed
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
references:
- kind: code
  role: implementation
  target: src/main/warroom/ipc.ts
- kind: code
  role: implementation
  target: src/main/warroom/engine.ts
- kind: code
  role: implementation
  target: src/renderer/warroom.js
---

# Dismiss idea

## Trigger

The user dismisses an idea.

## Outcome

Rice marks the idea dismissed.
