---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user opens a meeting
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice displays the meeting and its current working text
  kind: product
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Title
    - Date
    - Sessions
    - Language
    - Participants
    - Speaker names
    - Microphone
    - Audio
  - entity: notes
    effect: reads
    facts:
    - Content
    - Progress
  - entity: transcript
    effect: reads
    facts:
    - Content
    - Partial speech
    - Gaps
  - entity: annotations
    effect: reads
    facts:
    - Text
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
---

# Read meeting

## Trigger

The user opens a meeting.

## Outcome

Rice displays the meeting and its current working text.

## Edge cases

- An old note version is read-only until restored.
- Opening from a cross-meeting citation preserves the all-meetings chat scope.
