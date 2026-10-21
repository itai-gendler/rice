---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user opens a finding source
  kind: actor
  entities:
  - entity: finding
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice opens or reveals the finding source
  kind: product
  entities:
  - entity: finding
    effect: reads
    facts:
    - Source
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
- kind: code
  role: implementation
  target: src/main/warroom/source.ts
---

# Open finding source

## Trigger

The user opens a finding source.

## Outcome

Rice opens or reveals the finding source.

## Edge cases

- An unavailable or unsupported source produces a message.
