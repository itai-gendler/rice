---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user enters or clears a participant name
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice saves the meeting speaker names and applies them when presenting its transcript
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Speaker names
  - entity: transcript
    effect: reads
    facts:
    - Content
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
- kind: code
  role: implementation
  target: src/main/session/speaker-names.ts
- kind: code
  role: implementation
  target: src/shared/speakers.ts
---

# Name participant

## Trigger

The user enters or clears a participant name.

## Outcome

Rice saves the meeting speaker names and applies them when presenting its transcript.

## Edge cases

- Calendar participant names are offered as shortcuts.
