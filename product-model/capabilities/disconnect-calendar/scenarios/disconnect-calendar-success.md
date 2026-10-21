---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user disconnects the selected calendar connection
  kind: actor
  entities:
  - entity: calendar-connection
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::calendar
  actor: user
- text: Rice removes the calendar connection and its source events
  kind: product
  entities:
  - entity: calendar-connection
    effect: removes
  contexts:
    desktop:
      place: desktop::calendar
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
  target: src/main/calendar/calendar-feed.ts
- kind: code
  role: implementation
  target: src/main/calendar/ics-feed.ts
---

# Disconnect calendar

## Trigger

The user disconnects the selected calendar connection.

## Outcome

Rice removes the calendar connection and its source events.
