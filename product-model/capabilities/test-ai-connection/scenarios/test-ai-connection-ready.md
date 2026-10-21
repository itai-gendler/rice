---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user tests an AI connection
  kind: actor
  entities:
  - entity: ai-connection
    effect: reads
    facts:
    - Provider
    - Method
  contexts:
    desktop:
      place: desktop::ai
  actor: user
- text: Rice saves a successful AI connection test
  kind: product
  entities:
  - entity: ai-connection
    effect: changes
    facts:
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
- kind: code
  role: implementation
  target: src/main/ai/service.ts
---

# Confirm an AI connection

## Trigger

The user chooses Test connection.

## Outcome

Rice reports the AI connection ready and saves the successful result.
