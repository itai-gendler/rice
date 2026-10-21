---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user duplicates a note template
  kind: actor
  entities:
  - entity: note-template
    effect: reads
    facts:
    - Title
    - Description
    - Sections
    as: source
  contexts:
    desktop:
      place: desktop::note-templates
  actor: user
- text: Rice creates a personal note template copy and opens its editor
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
    as: copy
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

# Duplicate note template

## Trigger

The user duplicates a note template.

## Outcome

Rice creates a personal note template copy and opens its editor.
