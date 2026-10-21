---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: A capture source unexpectedly stops during an active recording.
  kind: condition
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  unattended: true
- text: Rice attempts bounded reconnection and marks the gap; persistent failure produces an actionable alert.
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
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

# Reconnect interrupted capture

## Trigger

A capture source unexpectedly stops during an active recording.

## Outcome

Rice attempts bounded reconnection and marks the gap; persistent failure produces an actionable alert.

## Edge cases

- Permission loss offers the relevant operating-system permission settings.
