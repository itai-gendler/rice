---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user turns audio keeping on or off
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::audio
  actor: user
- text: Rice saves whether later recordings keep their audio
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Audio settings
  contexts:
    desktop:
      place: desktop::audio
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
  target: src/renderer/settings.js
---

# Change audio settings

## Trigger

The user changes Keep meeting audio in Audio settings.

## Outcome

Later recordings keep or discard their audio according to the saved choice.
