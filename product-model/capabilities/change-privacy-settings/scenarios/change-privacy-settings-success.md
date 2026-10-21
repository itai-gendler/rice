---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user turns Fully local, Hide personal data or the consent reminder on or off, or picks a default retention
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::privacy
  actor: user
- text: Rice saves the privacy choices for later AI calls, retention sweeps and recording starts
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Fully local
    - Hide personal data
    - Default retention
    - Consent reminder
  contexts:
    desktop:
      place: desktop::privacy
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
  target: src/renderer/settings.js
---

# Change privacy settings

## Trigger

The user changes Fully local, Hide personal data, the default retention or the consent reminder in Privacy settings.

## Outcome

Later AI calls, retention sweeps and recording starts follow the saved privacy choices.
