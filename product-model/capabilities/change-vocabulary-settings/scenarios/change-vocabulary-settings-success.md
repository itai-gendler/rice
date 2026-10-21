---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user adds or removes vocabulary terms and chooses whether calendar attendees are included
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::vocabulary
  actor: user
- text: Rice saves the terms without repeats and the attendee choice for later transcription
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Vocabulary
  contexts:
    desktop:
      place: desktop::vocabulary
  actor: user
references:
- kind: code
  role: implementation
  target: src/renderer/renderer.js
- kind: code
  role: implementation
  target: src/main/app/main.ts
- kind: code
  role: implementation
  target: src/renderer/settings.js
---

# Change vocabulary settings

## Trigger

The user edits the names, clients and acronyms in Vocabulary settings.

## Outcome

Later transcription uses the saved terms, plus calendar attendees when that option is on.
