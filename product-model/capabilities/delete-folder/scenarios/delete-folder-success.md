---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user confirms deletion of a folder
  kind: actor
  entities:
  - entity: folder
    effect: reads
    facts: []
    as: selected
  contexts:
    desktop:
      place: desktop::library
  actor: user
- text: Rice removes the folder and promotes its meetings and child folders to its parent
  kind: product
  entities:
  - entity: folder
    effect: removes
    as: selected
  - entity: meeting
    effect: changes
    facts:
    - Folder
  - entity: folder
    effect: changes
    facts:
    - Parent
    - Name
    - Order
    as: promoted
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

# Delete folder

## Trigger

The user confirms deletion of a folder.

## Outcome

Rice removes the folder and promotes its meetings and child folders to its parent.

## Edge cases

- Folder operations leave physical meeting directories in place.
