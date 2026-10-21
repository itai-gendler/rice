---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user changes the meeting suggestion settings
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts: []
  - entity: settings
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice saves the meeting suggestion settings for the next cycle
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Ideas enabled
    - Ideas settings
  - entity: idea-template
    effect: reads
    facts:
    - Title
    - Instruction
    - Categories
  - entity: settings
    effect: reads
    facts: []
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

# Change ideas settings

## Trigger

The user changes the meeting suggestion settings.

## Outcome

Rice saves the meeting suggestion settings for the next cycle.
