---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user enters a replacement folder name
  kind: actor
  entities:
  - entity: folder
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::library
  actor: user
- text: Rice saves the folder name
  kind: product
  entities:
  - entity: folder
    effect: changes
    facts:
    - Name
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

# Rename folder

## Trigger

The user enters a replacement folder name.

## Outcome

Rice saves the folder name.

## Edge cases

- Folder operations leave physical meeting directories in place.
