---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user connects the macOS Calendar and allows Calendar access when macOS asks
  kind: actor
  entities:
  - entity: calendar-connection
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::calendar
  actor: user
- text: Rice reads upcoming events from the calendars on the Mac
  kind: product
  entities:
  - entity: calendar-connection
    effect: creates
    facts:
    - Source
    - Status
    - Calendars
    - Address label
  - entity: calendar-event
    effect: reads
    facts:
    - Title
    - Time
    - Participants
    - Join link
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
  target: src/main/calendar/google-auth.ts
- kind: code
  role: implementation
  target: src/main/calendar/ics-feed.ts
- kind: code
  role: implementation
  target: src/renderer/calendar-connect.js
---

# Connect macOS Calendar

## Trigger

The user chooses to connect the macOS Calendar in Calendar settings.

## Outcome

Calendar settings show macOS Calendar access as allowed, and its events appear on Home.

## Edge cases

- If Calendar access is declined, Calendar settings show it and no events appear.
