---
kind: validation
routes:
  desktop: Rice desktop
steps:
- text: The user chooses a destination folder
  kind: actor
  entities:
  - entity: folder
    effect: reads
    facts:
    - Name
    - Parent
  contexts:
    desktop:
      place: desktop::library
  actor: user
- text: Rice reports the invalid folder destination
  kind: product
  entities:
  - entity: folder
    effect: reads
    facts:
    - Parent
  contexts:
    desktop:
      place: desktop::library
  actor: user
references:
- kind: code
  role: implementation
  target: src/main/store/folders.ts
- kind: code
  role: implementation
  target: src/renderer/renderer.js
---

# Reject an invalid folder move

## Trigger

The user tries to place a folder below its own descendant or beyond four levels.

## Outcome

Rice reports the conflict and preserves the hierarchy.

## Edge cases

- A duplicate name among the new siblings also prevents the move.
