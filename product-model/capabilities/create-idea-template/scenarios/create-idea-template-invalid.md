---
kind: validation
routes:
  desktop: Rice desktop
steps:
- text: The user submits the idea template
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
- text: Rice reports invalid idea template content
  kind: product
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
references:
- kind: code
  role: implementation
  target: src/main/warroom/idea-templates.ts
- kind: code
  role: implementation
  target: src/renderer/idea-templates.js
---

# Reject invalid idea template content

## Trigger

The user saves content that fails the template limits.

## Outcome

Rice keeps the editor open with a validation message.

## Edge cases

- An idea template needs a nonempty instruction and at most six unique categories.
