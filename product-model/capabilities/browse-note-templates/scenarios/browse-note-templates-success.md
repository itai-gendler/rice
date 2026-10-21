---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user opens the note template list
  kind: actor
  entities:
  - entity: note-template
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::note-templates
  actor: user
- text: Rice displays the note templates
  kind: product
  entities:
  - entity: note-template
    effect: reads
    facts:
    - Title
    - Description
    - Sections
    - Built in
    - Customized
  contexts:
    desktop:
      place: desktop::note-templates
  actor: user
references:
- kind: code
  role: implementation
  target: src/main/templates/store.ts
- kind: code
  role: implementation
  target: src/main/templates/schema.ts
- kind: code
  role: implementation
  target: src/renderer/templates.js
---

# Browse note templates

## Trigger

The user opens the note template list.

## Outcome

Rice displays the note templates.
