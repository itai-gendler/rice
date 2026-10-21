---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses the meeting language
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice saves the meeting language for the next recording
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Language
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
---

# Change meeting language

## Trigger

The user chooses the meeting language.

## Outcome

Rice saves the meeting language for the next recording.
