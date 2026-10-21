---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user edits and saves the idea template
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
- text: Rice saves the idea template content
  kind: product
  entities:
  - entity: idea-template
    effect: changes
    facts:
    - Title
    - Description
    - Instruction
    - Categories
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

# Edit idea template

## Trigger

The user edits and saves the idea template.

## Outcome

Rice saves the idea template content.
