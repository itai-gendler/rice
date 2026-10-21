---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user selects another parent or the root for a folder
  kind: actor
  entities:
  - entity: folder
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::library
  actor: user
- text: Rice saves the folder parent and puts it last among its new siblings
  kind: product
  entities:
  - entity: folder
    effect: changes
    facts:
    - Parent
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

# Move folder

## Trigger

The user selects another parent or the root for a folder.

## Outcome

Rice saves the folder parent and puts it last among its new siblings.

## Edge cases

- Folder operations leave physical meeting directories in place.
