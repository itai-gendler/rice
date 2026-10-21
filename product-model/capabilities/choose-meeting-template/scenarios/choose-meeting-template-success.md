---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses a note template
  kind: actor
  entities:
  - entity: note-template
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice saves the meeting template choice and shows its sections
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Template
  - entity: note-template
    effect: reads
    facts:
    - Title
    - Description
    - Sections
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
  target: src/main/templates/store.ts
---

# Choose meeting template

## Trigger

The user chooses a note template.

## Outcome

Rice saves the meeting template choice and shows its sections.
