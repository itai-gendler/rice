---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The user selects the calendar event
  kind: actor
  entities:
  - entity: calendar-event
    effect: reads
    facts:
    - Title
    - Time
  contexts:
    desktop:
      place: desktop::home
  actor: user
- text: Rice opens the existing meeting
  kind: product
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Calendar event
    - Title
  - entity: annotations
    effect: reads
    facts:
    - Text
  contexts:
    desktop:
      place: desktop::meeting
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
  target: src/main/store/drafts.ts
---

# Open existing event notes

## Trigger

The user chooses Take notes for an event with an existing draft.

## Outcome

Rice opens that draft with its existing jottings.
