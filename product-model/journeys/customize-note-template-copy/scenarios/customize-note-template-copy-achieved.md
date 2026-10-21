---
kind: primary
result: achieved
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
  capability: duplicate-note-template
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
  capability: duplicate-note-template
- text: The user edits and saves the note template
  kind: actor
  entities:
  - entity: note-template
    effect: reads
    facts: []
    as: copy
  contexts:
    desktop:
      place: desktop::note-template-editor
  actor: user
  capability: edit-note-template
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
    as: copy
  contexts:
    desktop:
      place: desktop::note-template-editor
  actor: user
  capability: edit-note-template
references:
- kind: code
  role: implementation
  target: src/renderer/templates.js
---

# Customize a note template copy

## Trigger

The user duplicates a template to adapt it.

## Outcome

The independent copy opens in its editor and is saved with the new content.
