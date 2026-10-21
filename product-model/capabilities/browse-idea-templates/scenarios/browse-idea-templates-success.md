---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user opens the idea template list
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
      place: desktop::idea-templates
  actor: user
- text: Rice displays the idea templates
  kind: product
  entities:
  - entity: idea-template
    effect: reads
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
      place: desktop::idea-templates
  actor: user
references:
- kind: code
  role: implementation
  target: src/main/warroom/idea-templates.ts
- kind: code
  role: implementation
  target: src/renderer/idea-templates.js
---

# Browse idea templates

## Trigger

The user opens the idea template list.

## Outcome

Rice displays the idea templates.
