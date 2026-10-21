---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The ideas interval is due during enabled unpaused recording and enough new speech exists.
  kind: condition
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Ideas settings
    - Extra cycles
  - entity: idea
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  unattended: true
- text: Rice saves new suggestions and advances the meeting cycle count.
  kind: product
  entities:
  - entity: idea
    effect: creates
    facts:
    - Text
    - Time
    - Category
    - Template
    to: Suggested
  - entity: meeting
    effect: changes
    facts:
    - Ideas count
  - entity: transcript
    effect: reads
    facts:
    - Content
  - entity: idea-template
    effect: reads
    facts:
    - Instruction
    - Categories
  contexts:
    desktop:
      place: desktop::meeting
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

# Generate scheduled ideas

## Trigger

The ideas interval is due during enabled unpaused recording and enough new speech exists.

## Outcome

Rice saves new suggestions and advances the meeting cycle count.
