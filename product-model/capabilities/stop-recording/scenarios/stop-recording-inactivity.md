---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The configured silence limit is reached, and the warning has remained unanswered for two minutes.
  kind: condition
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Recording alerts
  contexts:
    desktop:
      place: desktop::meeting
  unattended: true
- text: Rice stops the meeting, finishes its material and offers Continue recording.
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Date
    - Sessions
    - Audio
    - Recording alerts
    - Capture in use
    - Capture running
    from: Recording
    to: Done
  - entity: transcript
    effect: changes
    facts:
    - Content
    - Gaps
  contexts:
    desktop:
      place: desktop::meeting
references:
- kind: code
  role: implementation
  target: src/main/session/meeting-session.ts
- kind: code
  role: implementation
  target: src/main/app/main.ts
---

# Stop after unanswered inactivity warning

## Trigger

The configured silence limit is reached, and the warning has remained unanswered for two minutes.

## Outcome

Rice stops the meeting, finishes its material and offers Continue recording.

## Edge cases

- The default silence threshold is fifteen minutes; zero disables this automatic policy.
- A manual pause does not count toward silence stopping.
