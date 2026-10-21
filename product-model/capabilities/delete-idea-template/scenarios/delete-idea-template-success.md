---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user confirms deletion of a personal idea template
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
- text: Rice removes the idea template
  kind: product
  entities:
  - entity: idea-template
    effect: removes
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

# Delete idea template

## Trigger

The user confirms deletion of a personal idea template.

## Outcome

Rice removes the idea template.

## Edge cases

- A deleted selection falls back to the shipped default when resolved for future use.
