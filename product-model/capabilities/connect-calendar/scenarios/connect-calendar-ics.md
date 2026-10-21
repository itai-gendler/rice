---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The user pastes the private link of a calendar
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::calendar
  actor: user
- text: Rice saves the subscription and reads the calendar’s events from that link
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

# Connect ICS

## Trigger

The user chooses Subscribe by link (ICS) in Calendar settings.

## Outcome

Calendar settings show the subscription by its domain and event count, and its events appear on Home.

## Edge cases

- A link that is not https or webcal, or that cannot be read, is refused with a message and nothing is saved.
- Rice reads the link again every ten minutes.
- While Fully local mode is on, a link cannot be added and a saved one is not read.
