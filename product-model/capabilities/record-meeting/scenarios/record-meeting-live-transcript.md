---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: Audio frames arrive during an unpaused recording.
  kind: condition
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  unattended: true
- text: Rice finalizes local speech with source labels and times while new partial speech can continue.
  kind: product
  entities:
  - entity: transcript
    effect: changes
    facts:
    - Content
    - Partial speech
  - entity: meeting
    effect: reads
    facts:
    - Language
    - Speaker names
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

# Transcribe arriving speech

## Trigger

Audio frames arrive during an unpaused recording.

## Outcome

Rice finalizes local speech with source labels and times while new partial speech can continue.
