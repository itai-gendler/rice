---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user requests an ICS calendar refresh
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::calendar
  actor: user
- text: Rice refreshes calendar events and reports calendar connection status
  kind: product
  entities:
  - entity: calendar-connection
    effect: changes
    facts:
    - Status
    - Calendars
  - entity: calendar-event
    effect: reads
    facts:
    - Title
    - Time
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

# Refresh calendar

## Trigger

The user requests an ICS calendar refresh.

## Outcome

Rice refreshes calendar events and reports calendar connection status.

## Edge cases

- Google refreshes about every five minutes; ICS about every ten minutes.
