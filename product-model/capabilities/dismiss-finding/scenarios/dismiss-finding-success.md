---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user dismisses a finding
  kind: actor
  entities:
  - entity: finding
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice marks the finding Dismissed
  kind: product
  entities:
  - entity: finding
    effect: changes
    facts:
    - Pinned
    from: Visible
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

# Dismiss finding

## Trigger

The user dismisses a finding.

## Outcome

Rice marks the finding Dismissed.

## Edge cases

- A short-lived Undo action restores visibility.
