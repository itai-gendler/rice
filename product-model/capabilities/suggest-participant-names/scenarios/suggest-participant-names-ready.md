---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user requests name suggestions
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice asks the AI using transcript context and shows the result
  kind: product
  entities:
  - entity: transcript
    effect: reads
    facts:
    - Content
  - entity: meeting
    effect: reads
    facts:
    - Speaker names
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
---

# Suggest names from speech

## Trigger

The user asks for participant name suggestions.

## Outcome

Rice shows suggestions for the user to choose.
