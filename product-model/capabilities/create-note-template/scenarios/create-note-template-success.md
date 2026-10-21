---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user enters the note template content and saves
  kind: actor
  entities:
  - entity: note-template
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::note-template-editor
  actor: user
- text: Rice creates the note template and returns to its list
  kind: product
  entities:
  - entity: note-template
    effect: creates
    facts:
    - Title
    - Description
    - Sections
    - Built in
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

# Create note template

## Trigger

The user enters the note template content and saves.

## Outcome

Rice creates the note template and returns to its list.
