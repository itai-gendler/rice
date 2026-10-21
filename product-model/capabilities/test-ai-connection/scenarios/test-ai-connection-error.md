---
kind: edge
routes:
  desktop: Rice desktop
steps:
- text: The user tests an AI connection
  kind: actor
  entities:
  - entity: ai-connection
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::ai
  actor: user
- text: Rice reports the AI connection failure
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

# Explain a failed connection

## Trigger

The user tests a connection with missing login, unavailable server or rejected credentials.

## Outcome

Rice saves and displays the failed result with the corrective action.
