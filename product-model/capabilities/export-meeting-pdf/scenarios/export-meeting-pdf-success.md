---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses the PDF filename, destination and whether to include the transcript
  kind: actor
  entities:
  - entity: transcript
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice writes the PDF and offers to reveal it
  kind: product
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Title
    - Date
    - Participants
    - Speaker names
  - entity: notes
    effect: reads
    facts:
    - Content
  - entity: transcript
    effect: reads
    facts:
    - Content
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
  target: src/main/share/pdf.ts
---

# Export meeting PDF

## Trigger

The user chooses the PDF filename, destination and whether to include the transcript.

## Outcome

Rice writes the PDF and offers to reveal it.

## Edge cases

- Existing filenames get a numeric suffix; export does not overwrite an earlier PDF.
- The last chosen export folder is remembered.
- A PDF write failure is reported.
- Historical note previews do not replace current notes in the PDF.
