---
kind: primary
result: achieved
routes:
  desktop: Rice desktop
steps:
- text: The user chooses New war room
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::home
  actor: user
  capability: create-meeting
- text: Rice creates a meeting in War room mode and opens Investigation
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
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
  capability: create-meeting
- text: The user changes investigation settings
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
  capability: change-investigation-settings
- text: Rice saves the meeting mode, investigation settings and extra cycle allowance
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Mode
    - Investigation active
    - Investigation settings
    - Extra cycles
    - Cycle ceiling
  - entity: settings
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
  capability: change-investigation-settings
references:
- kind: code
  role: implementation
  target: src/renderer/renderer.js
- kind: code
  role: implementation
  target: src/main/app/main.ts
- kind: code
  role: implementation
  target: src/renderer/warroom.js
---

# Prepare a War room

## Trigger

The user chooses New war room.

## Outcome

The new meeting opens at Investigation and its source and interval choices are saved.
