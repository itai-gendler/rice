---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Join for a calendar event
  kind: actor
  entities:
  - entity: calendar-event
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::home
  actor: user
- text: Rice opens the calendar event join link
  kind: product
  entities:
  - entity: calendar-event
    effect: reads
    facts:
    - Join link
  contexts:
    desktop:
      place: desktop::home
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
  target: src/renderer/home.js
---

# Join calendar event

## Trigger

The user chooses Join for a calendar event.

## Outcome

Rice opens the calendar event join link.
