---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The user sends a question with web search
  kind: actor
  entities:
  - entity: meeting-chat
    effect: reads
    facts:
    - Web search
  contexts:
    desktop:
      place: desktop::chat
  actor: user
- text: Rice asks the configured AI with transcript context and web search
  kind: product
  entities:
  - entity: transcript
    effect: reads
    facts:
    - Content
  - entity: settings
    effect: reads
    facts:
    - AI provider
  contexts:
    desktop:
      place: desktop::chat
  actor: user
- text: Rice saves the meeting chat answer with web sources
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

# Ask with web search

## Trigger

The user sends a question with Search the web enabled and supported.

## Outcome

Rice answers with the selected provider’s web search and saves external source links.

## Edge cases

- The same web-source retention applies to all-meetings chat.
