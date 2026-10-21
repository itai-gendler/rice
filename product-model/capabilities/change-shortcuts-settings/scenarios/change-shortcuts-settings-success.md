---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user picks a recording shortcut or None
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::shortcuts
  actor: user
- text: Rice registers the chosen shortcut and saves it
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Shortcut
  contexts:
    desktop:
      place: desktop::shortcuts
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

# Change shortcuts settings

## Trigger

The user changes the global recording shortcut in Shortcuts settings.

## Outcome

The chosen shortcut starts and stops recording from any app, or no shortcut is registered for None.
