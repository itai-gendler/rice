---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses a note template as the default
  kind: actor
  entities:
  - entity: note-template
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::note-templates
  actor: user
- text: Rice saves the template as the default in settings
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Default template
  - entity: note-template
    effect: reads
    facts:
    - Title
  contexts:
    desktop:
      place: desktop::note-templates
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
  target: src/renderer/templates.js
---

# Choose default template

## Trigger

The user chooses a note template as the default.

## Outcome

Rice saves the template as the default in settings.
