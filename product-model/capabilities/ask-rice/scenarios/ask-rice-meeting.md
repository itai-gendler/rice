---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user asks about the meeting
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Title
  contexts:
    desktop:
      place: desktop::chat
  actor: user
- text: Rice prepares transcript, annotations, prior chat and available attachment text
  kind: product
  entities:
  - entity: transcript
    effect: reads
    facts:
    - Content
  - entity: annotations
    effect: reads
    facts:
    - Text
  - entity: meeting-chat
    effect: reads
    facts:
    - Turns
  - entity: attachment
    effect: reads
    facts:
    - Extracted text
  - entity: memory-fact
    effect: reads
    facts:
    - Text
    - Source
  contexts:
    desktop:
      place: desktop::chat
  actor: user
- text: Rice streams and saves the completed meeting chat answer
  kind: product
  entities:
  - entity: meeting-chat
    effect: changes
    facts:
    - Turns
    - Web sources
    - Answer progress
  - entity: meeting
    effect: reads
    facts: []
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
  target: src/main/search/global-chat.ts
- kind: code
  role: implementation
  target: src/main/search/retrieve.ts
- kind: code
  role: implementation
  target: src/main/session/chat-context.ts
- kind: code
  role: implementation
  target: src/main/store/global-chat.ts
---

# Ask about this meeting

## Trigger

The user sends a question in This meeting chat.

## Outcome

Rice streams and saves an answer grounded in the meeting context.

## Edge cases

- Long transcripts use saved part summaries and relevant passages within the active context budget.
- When there are no useful matching keywords, recent transcript passages supply context.
- Image attachments accompany questions through supported image-capable API or local providers.
- War room chat includes prioritized visible findings and uses its selected supported sources.
