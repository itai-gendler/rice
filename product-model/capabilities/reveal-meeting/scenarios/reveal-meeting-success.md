---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Show in Finder or its platform equivalent
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice opens the meeting directory in the system file manager
  kind: product
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Title
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
references:
- kind: code
  role: implementation
  target: src/renderer/renderer.js
- kind: code
  role: implementation
  target: src/main/app/main.ts
---

# Show meeting files

## Trigger

The user chooses Show in Finder or its platform equivalent.

## Outcome

Rice opens the meeting directory in the system file manager.
