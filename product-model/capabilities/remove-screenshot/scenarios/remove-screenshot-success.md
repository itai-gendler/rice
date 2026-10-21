---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user removes a screenshot
  kind: actor
  entities:
  - entity: screenshot
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice removes the selected screenshot
  kind: product
  entities:
  - entity: screenshot
    effect: removes
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
  target: src/main/screenshots/store.ts
- kind: code
  role: implementation
  target: src/main/screenshots/ipc.ts
---

# Remove screenshot

## Trigger

The user removes a screenshot.

## Outcome

Rice removes the selected screenshot.
