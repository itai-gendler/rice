---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user opens Home
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::home
  actor: user
- text: Rice displays calendar events and their meeting actions
  kind: product
  entities:
  - entity: calendar-event
    effect: reads
    facts:
    - Title
    - Time
    - Participants
    - Join link
    - Source
  - entity: meeting
    effect: reads
    facts: []
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
- kind: code
  role: implementation
  target: src/main/calendar/calendar-feed.ts
---

# Browse calendar

## Trigger

The user opens Home.

## Outcome

Rice displays calendar events and their meeting actions.

## Edge cases

- All-day events are displayed without recording prompts.
