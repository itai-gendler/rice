---
kind: validation
routes:
  desktop: Rice desktop
steps:
- text: The user submits a folder name
  kind: actor
  entities:
  - entity: folder
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::library
  actor: user
- text: Rice reports the folder naming conflict
  kind: product
  entities:
  - entity: folder
    effect: reads
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

# Reject an invalid folder name

## Trigger

The user submits an empty, overlong or duplicate sibling name.

## Outcome

Rice explains the invalid name without creating a folder.
