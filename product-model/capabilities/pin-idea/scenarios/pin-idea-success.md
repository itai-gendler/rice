---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user pins an idea
  kind: actor
  entities:
  - entity: idea
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice pins the idea and appends its text under Ideas in annotations
  kind: product
  entities:
  - entity: idea
    effect: changes
    facts: []
    from: Suggested
    to: Pinned
  - entity: annotations
    effect: changes
    facts:
    - Text
    - Times
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

# Pin idea

## Trigger

The user pins an idea.

## Outcome

Rice pins the idea and appends its text under Ideas in annotations.
