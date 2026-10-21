---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user requests ideas now
  kind: actor
  entities:
  - entity: idea
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice reads new transcript context and the idea template
  kind: product
  entities:
  - entity: transcript
    effect: reads
    facts:
    - Content
    - Partial speech
  - entity: idea-template
    effect: reads
    facts:
    - Instruction
    - Categories
  - entity: idea
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice creates suggestions and increments the meeting ideas count
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

# Generate ideas now

## Trigger

The user chooses Generate now during an enabled unpaused recording.

## Outcome

Rice saves new suggestions with their type and template.

## Edge cases

- Too little new speech produces a no-new-speech notice rather than another AI call.
- The live-cycle limit is counted separately for ideas and investigation.
