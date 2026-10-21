---
kind: alternate
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

# Prepare a War room

## Trigger

The user chooses New war room.

## Outcome

The meeting opens with Investigation selected.
