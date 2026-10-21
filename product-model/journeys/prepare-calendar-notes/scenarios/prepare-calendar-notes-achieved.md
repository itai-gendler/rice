---
kind: primary
result: achieved
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
  capability: create-meeting
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
  capability: create-meeting
- text: The user edits annotations
  kind: actor
  entities:
  - entity: annotations
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
  capability: edit-annotations
- text: Rice saves annotations and their line times
  kind: product
  entities:
  - entity: annotations
    effect: changes
    facts:
    - Text
    - Times
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
  capability: edit-annotations
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

# Prepare notes for a calendar meeting

## Trigger

The user chooses Take notes on a calendar event.

## Outcome

The event-linked draft opens and contains saved annotations.
