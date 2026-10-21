---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user removes the AI connection credential
  kind: actor
  entities:
  - entity: ai-connection
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::ai
  actor: user
- text: Rice clears the AI connection credential and test result
  kind: product
  entities:
  - entity: ai-connection
    effect: changes
    facts:
    - Credential status
    - Test result
  contexts:
    desktop:
      place: desktop::ai
  actor: user
references:
- kind: code
  role: implementation
  target: src/renderer/renderer.js
- kind: code
  role: implementation
  target: src/main/app/main.ts
---

# Remove AI credentials

## Trigger

The user removes the AI connection credential.

## Outcome

Rice clears the AI connection credential and test result.
