---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: Storage fills or the chosen meeting directory disappears during recording.
  kind: condition
  entities:
  - entity: meeting
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  unattended: true
- text: Rice reports the storage problem and preserves available text through its local recovery copy.
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Audio
    - Recording alerts
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
- kind: code
  role: implementation
  target: src/main/app/record-shortcut.ts
- kind: code
  role: implementation
  target: src/main/session/prompt-policy.ts
---

# Handle unavailable recording storage

## Trigger

Storage fills or the chosen meeting directory disappears during recording.

## Outcome

Rice reports the storage problem and preserves available text through its local recovery copy.

## Edge cases

- Audio that could not be saved is represented as a gap.
- Rice retries storage and clears the alert when writing becomes possible; a fallback location is reported when used.
