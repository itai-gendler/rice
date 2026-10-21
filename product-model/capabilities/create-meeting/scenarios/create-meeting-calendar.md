---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The user selects a calendar event
  kind: actor
  entities:
  - entity: calendar-event
    effect: reads
    facts:
    - Title
    - Time
    - Participants
  contexts:
    desktop:
      place: desktop::home
  actor: user
- text: Rice prepares a meeting with the event title and participants and opens it
  kind: product
  entities:
  - entity: meeting
    effect: creates
    facts:
    - Title
    - Date
    - Sessions
    - Capture in use
    - Capture running
    - Ideas enabled
    - Investigation active
    - Language
    - Template
    - Folder
    - Participants
    - Speaker names
    - Audio
    - Microphone
    - Consent copied
    - Calendar event
    - Recording alerts
    - Mode
    - Ideas settings
    - Investigation settings
    - Extra cycles
    - Ideas count
    - Investigation count
    - Cycle ceiling
    to: Draft
  - entity: transcript
    effect: creates
    facts:
    - Content
    - Partial speech
    - Gaps
    with: meeting
  - entity: annotations
    effect: creates
    facts:
    - Text
    - Times
    with: meeting
  - entity: notes
    effect: creates
    facts:
    - Content
    - Progress
    to: Empty
    with: meeting
  - entity: calendar-event
    effect: reads
    facts:
    - Title
    - Participants
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

# Prepare notes for an event

## Trigger

The user chooses Take notes for a calendar event.

## Outcome

The existing draft for that event, or a newly created one, opens at the meeting.
