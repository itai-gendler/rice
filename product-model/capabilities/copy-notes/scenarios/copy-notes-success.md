---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Copy notes or Copy as Markdown
  kind: actor
  entities:
  - entity: notes
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice copies the current notes to the clipboard
  kind: product
  entities:
  - entity: notes
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
---

# Copy notes

## Trigger

The user chooses Copy notes or Copy as Markdown.

## Outcome

Rice copies the current notes to the clipboard.

## Edge cases

- Empty notes produce a no-notes message.
- Viewing a historical version does not change which notes are copied.
