---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses the active AI, its model, the light model, local server options or the live-cycle limit
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::ai
  actor: user
- text: Rice saves the app-wide AI choices that later AI requests use
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - AI provider
    - AI model
    - Light model
    - Local server
    - Cycle limit
  contexts:
    desktop:
      place: desktop::ai
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

# Change artificial intelligence settings

## Trigger

The user changes the active AI, a model, local server options or the live-cycle limit in Artificial intelligence settings.

## Outcome

The next notes, questions and live cycles use the saved AI choices.
