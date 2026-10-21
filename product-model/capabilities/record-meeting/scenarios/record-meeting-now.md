---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Record now
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::home
  actor: user
- text: Rice selects an ongoing event or one starting within ten minutes when available
  kind: product
  entities:
  - entity: calendar-event
    effect: reads
    facts:
    - Title
    - Time
    - Participants
  - entity: meeting
    effect: reads
    facts:
    - Calendar event
  contexts:
    desktop:
      place: desktop::home
  actor: user
- text: Rice starts a new meeting and opens its recording
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

# Record now from Home or the shortcut

## Trigger

The user chooses Record now or uses the global recording shortcut.

## Outcome

Rice starts the current or imminent calendar meeting draft, or a new meeting.

## Edge cases

- An existing calendar draft is adopted rather than duplicated.
- Pressing the same shortcut during recording stops the active recording.
