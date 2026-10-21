---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user saves the last question or enters a saved question
  kind: actor
  entities:
  - entity: saved-question
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::chat
  actor: user
- text: Rice adds the saved question to the personal picker
  kind: product
  entities:
  - entity: saved-question
    effect: creates
    facts:
    - Text
  contexts:
    desktop:
      place: desktop::chat
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
  target: src/shared/saved-prompts.ts
- kind: code
  role: implementation
  target: src/renderer/prompts-menu.js
---

# Save question

## Trigger

The user saves the last question or enters a saved question.

## Outcome

Rice adds the saved question to the personal picker.

## Edge cases

- Questions normalize whitespace and are limited to 300 characters.
- Duplicates ignoring case do not create another entry; at most eight personal questions are retained.
