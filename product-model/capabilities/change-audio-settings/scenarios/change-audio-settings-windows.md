---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The user changes Windows microphone and transcription settings
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::audio
  actor: user
- text: Rice saves audio settings and reports whether they apply now or after recording
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

# Choose Windows input and transcription

## Trigger

Rice is running on Windows and the user opens Audio settings.

## Outcome

Rice saves microphone, model-tier and GPU choices with their effective timing.
