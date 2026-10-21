---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The user sends a question
  kind: actor
  entities:
  - entity: all-meetings-chat
    effect: reads
    facts:
    - Scope
  contexts:
    desktop:
      place: desktop::chat
  actor: user
- text: Rice selects recent meetings and current notes within the requested scope
  kind: product
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Title
    - Date
    - Folder
  - entity: notes
    effect: reads
    facts:
    - Content
  contexts:
    desktop:
      place: desktop::chat
  actor: user
- text: Rice saves the warning and answer with the fallback citations
  kind: product
  entities:
  - entity: all-meetings-chat
    effect: changes
    facts:
    - Turns
    - Scope
    - Citations
    - Answer progress
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

# Answer with an explicit recent-meeting fallback

## Trigger

No meeting in the requested scope and period mentions the useful question terms.

## Outcome

Rice warns that no matching meeting was found and uses recent eligible meetings.
