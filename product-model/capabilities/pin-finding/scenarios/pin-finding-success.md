---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user pins a finding
  kind: actor
  entities:
  - entity: finding
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice marks the finding pinned
  kind: product
  entities:
  - entity: finding
    effect: changes
    facts:
    - Pinned
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

# Pin finding

## Trigger

The user pins a finding.

## Outcome

Rice marks the finding pinned.
