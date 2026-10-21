---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The user changes automatic or fixed microphone settings
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::audio
  actor: user
- text: Rice saves audio settings
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

# Choose macOS input behavior

## Trigger

Rice is running on macOS and the user opens Audio settings.

## Outcome

Rice saves automatic selection or a fixed microphone choice.

## Edge cases

- Automatic selection prefers a real input already in use, then a voiced candidate, then the system default.
- A fixed available input takes precedence over automatic selection.
