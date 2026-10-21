---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The user accepts a recording offer
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::recording-alert
  actor: user
- text: Rice creates a recording meeting with the offered context
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
    to: Recording
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
  target: src/main/session/meeting-session.ts
- kind: code
  role: implementation
  target: src/main/app/main.ts
- kind: code
  role: implementation
  target: src/main/app/record-shortcut.ts
- kind: code
  role: implementation
  target: src/main/session/prompt-policy.ts
---

# Accept a recording offer

## Trigger

Rice detects a qualifying call or imminent calendar event.

## Outcome

Accepting the offer starts a meeting; Join and record also opens the call link.

## Edge cases

- All-day calendar events do not trigger recording offers.
- Browser microphone use needs current calendar evidence before Rice offers recording.
- Explicitly declining an app offer suppresses another offer for that app for twenty minutes.
