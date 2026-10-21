---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user confirms deletion of a personal note template
  kind: actor
  entities:
  - entity: note-template
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::note-templates
  actor: user
- text: Rice removes the note template
  kind: product
  entities:
  - entity: note-template
    effect: removes
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

# Delete note template

## Trigger

The user confirms deletion of a personal note template.

## Outcome

Rice removes the note template.

## Edge cases

- A deleted selection falls back to the shipped default when resolved for future use.
