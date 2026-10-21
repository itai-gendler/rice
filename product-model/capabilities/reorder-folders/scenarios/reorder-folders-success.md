---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user changes the order of sibling folders
  kind: actor
  entities:
  - entity: folder
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::library
  actor: user
- text: Rice saves the folder order among siblings
  kind: product
  entities:
  - entity: folder
    effect: changes
    facts:
    - Order
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

# Reorder folders

## Trigger

The user changes the order of sibling folders.

## Outcome

Rice saves the folder order among siblings.

## Edge cases

- Folder operations leave physical meeting directories in place.
