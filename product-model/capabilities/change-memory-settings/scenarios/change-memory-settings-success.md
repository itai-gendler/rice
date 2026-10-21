---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user turns Memory on or off
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::memory-settings
  actor: user
- text: Rice saves whether memory extraction and recall run, keeping the facts already stored
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Memory enabled
  contexts:
    desktop:
      place: desktop::memory-settings
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

# Change memory settings

## Trigger

The user changes the Memory option in Memory settings.

## Outcome

Memory extraction and recall follow the saved choice, and stored facts stay until erased.
