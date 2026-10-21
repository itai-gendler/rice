---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The user asks in the selected scope
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
- text: Rice selects relevant meetings from the question period, folder and words
  kind: product
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Title
    - Date
    - Folder
  - entity: folder
    effect: reads
    facts:
    - Name
    - Parent
  - entity: notes
    effect: reads
    facts:
    - Content
  - entity: transcript
    effect: reads
    facts:
    - Content
  - entity: memory-fact
    effect: reads
    facts:
    - Text
    - Source
  contexts:
    desktop:
      place: desktop::chat
  actor: user
- text: Rice streams the answer and saves the all meetings chat with citations
  kind: product
  entities:
  - entity: all-meetings-chat
    effect: changes
    facts:
    - Turns
    - Scope
    - Citations
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

# Ask across meetings

## Trigger

The user asks in All meetings or a folder scope.

## Outcome

The saved answer includes links to its selected source meetings.

## Edge cases

- A selected folder includes its descendant folders.
- An explicit folder selection takes precedence over folder names mentioned in the question.
- Ordinary keyword retrieval selects at most eight meetings; generic or fallback retrieval selects at most five.
- A period with no eligible meetings is not broadened outside that period.
