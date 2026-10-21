---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user confirms Restore default
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::note-template-editor
  actor: user
- text: Rice restores the built-in note template
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

# Restore note template

## Trigger

The user confirms Restore default.

## Outcome

Rice restores the built-in note template.
