---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user duplicates a idea template
  kind: actor
  entities:
  - entity: idea-template
    effect: reads
    facts:
    - Title
    - Description
    - Instruction
    - Categories
    as: source
  - entity: idea
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::idea-templates
  actor: user
- text: Rice creates a personal idea template copy and opens its editor
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
    as: copy
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

# Duplicate idea template

## Trigger

The user duplicates a idea template.

## Outcome

Rice creates a personal idea template copy and opens its editor.
