---
kind: validation
routes:
  desktop: Rice desktop
steps:
- text: The user enters a shortcut
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::shortcuts
  actor: user
- text: Rice reports the conflict without changing settings
  kind: product
  entities:
  - entity: settings
    effect: reads
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

# Keep the previous shortcut on conflict

## Trigger

The user chooses a shortcut already taken by another application.

## Outcome

Rice reports the conflict and preserves the previous saved choice.
