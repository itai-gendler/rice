---
kind: primary
result: achieved
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
  capability: create-meeting
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
---

# Prepare a meeting for notes

## Trigger

The user creates a meeting to jot down points before recording.

## Outcome

The newly opened draft contains saved annotations.
