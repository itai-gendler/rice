---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user enters the idea template content and saves
  kind: actor
  entities:
  - entity: idea-template
    effect: reads
    facts: []
  - entity: idea
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::idea-template-editor
  actor: user
- text: Rice creates the idea template and returns to its list
  kind: product
  entities:
  - entity: idea-template
    effect: creates
    facts:
    - Title
    - Description
    - Instruction
    - Categories
    - Built in
    - Customized
  - entity: idea
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::idea-template-editor
  actor: user
references:
- kind: code
  role: implementation
  target: src/main/warroom/idea-templates.ts
- kind: code
  role: implementation
  target: src/renderer/idea-templates.js
---

# Create idea template

## Trigger

The user enters the idea template content and saves.

## Outcome

Rice creates the idea template and returns to its list.
