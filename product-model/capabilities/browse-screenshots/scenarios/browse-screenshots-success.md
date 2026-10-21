---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user opens a screenshot
  kind: actor
  entities:
  - entity: screenshot
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice displays the screenshot image and context
  kind: product
  entities:
  - entity: screenshot
    effect: reads
    facts:
    - Image
    - Time
    - Caption
    - Trigger
    - Transcript position
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
- kind: code
  role: implementation
  target: src/main/screenshots/ipc.ts
- kind: code
  role: implementation
  target: src/renderer/screenshots.js
---

# Browse screenshots

## Trigger

The user opens a screenshot.

## Outcome

Rice displays the screenshot image and context.
