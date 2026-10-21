---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user asks for a new meeting
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::home
  actor: user
- text: Rice creates the meeting and its empty working text, then opens it
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

# Prepare a new meeting

## Trigger

The user chooses New meeting.

## Outcome

The draft opens for annotations and recording.
