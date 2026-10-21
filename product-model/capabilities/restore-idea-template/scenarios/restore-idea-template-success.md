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
      place: desktop::idea-template-editor
  actor: user
- text: Rice restores the built-in idea template
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

# Restore idea template

## Trigger

The user confirms Restore default.

## Outcome

Rice restores the built-in idea template.
