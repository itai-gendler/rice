---
kind: primary
result: achieved
routes:
  desktop: Rice desktop
steps:
- text: The user duplicates an idea template
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
  capability: duplicate-idea-template
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
  capability: duplicate-idea-template
- text: The user edits and saves the idea template
  kind: actor
  entities:
  - entity: idea-template
    effect: reads
    facts: []
    as: copy
  - entity: idea
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::idea-template-editor
  actor: user
  capability: edit-idea-template
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
    as: copy
  - entity: idea
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::idea-template-editor
  actor: user
  capability: edit-idea-template
references:
- kind: code
  role: implementation
  target: src/renderer/idea-templates.js
---

# Customize an idea template copy

## Trigger

The user duplicates a template to adapt it.

## Outcome

The independent copy opens in its editor and is saved with the new content.
