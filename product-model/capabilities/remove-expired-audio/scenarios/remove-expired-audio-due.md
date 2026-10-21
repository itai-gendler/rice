---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The startup or daily sweep finds completed meeting audio past its effective retention period.
  kind: condition
  entities:
  - entity: folder
    effect: reads
    facts:
    - Audio retention
  - entity: settings
    effect: reads
    facts:
    - Default retention
  - entity: meeting
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  unattended: true
- text: Rice moves expired audio to Trash, retaining the meeting text and reporting the applied rule.
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Audio
  contexts:
    desktop:
      place: desktop::meeting
references:
- kind: code
  role: implementation
  target: src/renderer/renderer.js
- kind: code
  role: implementation
  target: src/main/app/main.ts
- kind: code
  role: implementation
  target: src/main/privacy/retention.ts
- kind: code
  role: implementation
  target: src/main/privacy/folder-rules.ts
---

# Apply audio retention

## Trigger

The startup or daily sweep finds completed meeting audio past its effective retention period.

## Outcome

Rice moves expired audio to Trash, retaining the meeting text and reporting the applied rule.

## Edge cases

- Audio expiry is measured from the latest end time, falling back to the start time.
- Whole-meeting expiry takes precedence when both deadlines have passed.
