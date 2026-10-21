---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user requests an email draft
  kind: actor
  entities:
  - entity: notes
    effect: reads
    facts:
    - Content
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice asks the AI using notes and meeting details
  kind: product
  entities:
  - entity: notes
    effect: reads
    facts:
    - Content
  - entity: meeting
    effect: reads
    facts:
    - Title
    - Date
    - Language
    - Participants
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice presents transient editable email text
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
references:
- kind: code
  role: implementation
  target: src/main/share/actions.ts
- kind: code
  role: implementation
  target: src/renderer/share.js
- kind: code
  role: implementation
  target: src/main/share/mailto.ts
---

# Draft an email from notes

## Trigger

The user chooses Follow-up email draft.

## Outcome

Rice presents an editable subject, body and calendar-derived recipients.
