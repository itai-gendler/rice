---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Undo after dismissing a finding
  kind: actor
  entities:
  - entity: finding
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice restores the finding to the visible results
  kind: product
  entities:
  - entity: finding
    effect: changes
    facts: []
    from: Dismissed
    to: Visible
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

# Undo finding dismissal

## Trigger

The user chooses Undo after dismissing a finding.

## Outcome

Rice restores the finding to the visible results.
