---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Record for the meeting
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Title
    - Language
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice starts the meeting recording and local transcription
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Date
    - Sessions
    - Microphone
    - Audio
    - Capture in use
    - Capture running
    from: Draft
    to: Recording
  - entity: transcript
    effect: changes
    facts:
    - Content
    - Partial speech
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

# Record a prepared meeting

## Trigger

The user chooses Record in a draft.

## Outcome

The meeting is recording and live speech appears as it becomes available.

## Edge cases

- An unavailable microphone permission produces an actionable recording error.
- A capture startup failure leaves an adopted draft available to retry.
- Less than 1 GB of free space produces a warning.
