---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses the folder privacy and retention values
  kind: actor
  entities:
  - entity: folder
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::library
  actor: user
- text: Rice saves the folder policy choices
  kind: product
  entities:
  - entity: folder
    effect: changes
    facts:
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
- kind: code
  role: implementation
  target: src/main/privacy/folder-rules.ts
---

# Change folder privacy

## Trigger

The user chooses the folder privacy and retention values.

## Outcome

Rice saves the folder policy choices.

## Edge cases

- Sensitivity inherited from an ancestor continues to apply.
- Each retention dimension inherits independently; explicit Keep forever overrides that inherited dimension.
