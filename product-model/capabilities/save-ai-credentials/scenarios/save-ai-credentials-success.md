---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user enters a supported AI connection credential
  kind: actor
  entities:
  - entity: ai-connection
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::ai
  actor: user
- text: Rice saves the AI connection credential and clears its previous test result
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
- kind: code
  role: implementation
  target: src/main/ai/service.ts
---

# Save AI credentials

## Trigger

The user enters a supported AI connection credential.

## Outcome

Rice saves the AI connection credential and clears its previous test result.

## Edge cases

- Invalid credential formats produce a validation message.
- If encrypted credential storage is unavailable, the credential is not saved.
