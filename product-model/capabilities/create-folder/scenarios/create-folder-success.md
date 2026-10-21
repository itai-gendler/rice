---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user enters a folder name and optional parent
  kind: actor
  entities:
  - entity: folder
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::library
  actor: user
- text: Rice creates the folder at the end of its siblings
  kind: product
  entities:
  - entity: folder
    effect: creates
    facts:
    - Name
    - Parent
    - Order
    - Sensitive
    - Audio retention
    - Meeting retention
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

# Create folder

## Trigger

The user enters a folder name and optional parent.

## Outcome

Rice creates the folder at the end of its siblings.

## Edge cases

- Folder operations leave physical meeting directories in place.
