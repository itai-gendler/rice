---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user turns screen capture on after reading its notice, or turns it off
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::screenshots-settings
  actor: user
- text: Rice saves whether captures may be taken during recording and shows the screen-recording permission status
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Screenshots enabled
  contexts:
    desktop:
      place: desktop::screenshots-settings
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

# Change screenshots settings

## Trigger

The user changes the Screenshots option in Screenshots settings.

## Outcome

Screenshots are taken during later unpaused recording only while the option is on.
