---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user turns Identify participants on or off
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::participants
  actor: user
- text: Rice saves whether later recordings tell the voices of other participants apart
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Identify participants
  contexts:
    desktop:
      place: desktop::participants
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

# Change participants settings

## Trigger

The user changes Identify participants in Participants settings.

## Outcome

Later recordings label other voices as numbered participants when the option is on.
