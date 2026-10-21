---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user opens How to use Rice
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::guide
  actor: user
- text: Rice shows current setup readiness and the relevant setup actions
  kind: product
  entities:
  - entity: settings
    effect: reads
    facts:
    - Meetings folder
  - entity: ai-connection
    effect: reads
    facts:
    - Provider
    - Test result
  contexts:
    desktop:
      place: desktop::guide
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
  target: src/renderer/onboarding.js
---

# Read setup guide

## Trigger

The user opens How to use Rice.

## Outcome

Rice shows current setup readiness and the relevant setup actions.

## Edge cases

- The guide can open operating-system permission settings or the relevant Rice settings subject.
