---
kind: validation
routes:
  desktop: Rice desktop
steps:
- text: The user submits the note template
  kind: actor
  entities:
  - entity: note-template
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::note-template-editor
  actor: user
- text: Rice reports invalid note template content
  kind: product
  entities:
  - entity: note-template
    effect: reads
    facts: []
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

# Reject invalid note template content

## Trigger

The user saves content that fails the template limits.

## Outcome

Rice keeps the editor open with a validation message.

## Edge cases

- A note template needs one to twelve sections with nonempty headings.
