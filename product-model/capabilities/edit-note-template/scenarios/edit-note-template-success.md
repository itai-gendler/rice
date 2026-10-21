---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user edits and saves the note template
  kind: actor
  entities:
  - entity: note-template
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::note-template-editor
  actor: user
- text: Rice saves the note template content
  kind: product
  entities:
  - entity: note-template
    effect: changes
    facts:
    - Title
    - Description
    - Sections
    - Customized
  contexts:
    desktop:
      place: desktop::note-template-editor
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

# Edit note template

## Trigger

The user edits and saves the note template.

## Outcome

Rice saves the note template content.
