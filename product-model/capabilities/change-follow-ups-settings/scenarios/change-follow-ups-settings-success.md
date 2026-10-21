---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user turns follow-up reminders on or off
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::follow-ups-settings
  actor: user
- text: Rice saves whether it reminds the user when their own follow-ups are due
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Follow-up notifications
  contexts:
    desktop:
      place: desktop::follow-ups-settings
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

# Change follow-ups settings

## Trigger

The user changes the follow-up reminder option in Follow-ups settings.

## Outcome

Rice shows or stops showing a local reminder when the user’s own follow-ups are due.
