---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The user chooses to connect Google and authorizes read access in the browser
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::calendar
  actor: user
- text: Rice keeps the Google connection and reads its upcoming events
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

# Connect Google

## Trigger

The user chooses to connect Google directly in Calendar settings.

## Outcome

Calendar settings show Google as connected, with its calendar count, and its events appear on Home.

## Edge cases

- Declined authorization or a network failure produces a connection message.
- While Fully local mode is on, connecting Google is unavailable.
