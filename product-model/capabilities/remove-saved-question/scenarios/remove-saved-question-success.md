---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user removes a saved question
  kind: actor
  entities:
  - entity: saved-question
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::chat
  actor: user
- text: Rice removes the selected saved question
  kind: product
  entities:
  - entity: saved-question
    effect: removes
  contexts:
    desktop:
      place: desktop::chat
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
  target: src/shared/saved-prompts.ts
- kind: code
  role: implementation
  target: src/renderer/prompts-menu.js
---

# Remove saved question

## Trigger

The user removes a saved question.

## Outcome

Rice removes the selected saved question.
