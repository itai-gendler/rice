---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user adds files or pastes an image
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice copies each attachment locally and extracts supported text
  kind: product
  entities:
  - entity: attachment
    effect: creates
    facts:
    - Name
    - Content
    - Size
    - Kind
    - Added
    - Extracted text
    - Text availability
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
- kind: code
  role: implementation
  target: src/main/attachments/store.ts
- kind: code
  role: implementation
  target: src/main/attachments/ipc.ts
- kind: code
  role: implementation
  target: src/renderer/attachments.js
---

# Add attachment

## Trigger

The user adds files or pastes an image.

## Outcome

Rice copies each attachment locally and extracts supported text.

## Edge cases

- A file may be at most 50 MiB and the meeting attachment total at most 500 MiB.
- Duplicate filenames get a suffix.
- A PDF without extractable text stays attached with a text-unavailable indication.
- During recording the attachment also receives a transcript marker.
