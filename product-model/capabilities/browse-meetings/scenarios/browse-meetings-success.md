---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user browses or searches saved meetings
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::library
  actor: user
- text: Rice shows matching meetings with dates, source fields and snippets
  kind: product
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Title
    - Date
  - entity: notes
    effect: reads
    facts:
    - Content
  - entity: transcript
    effect: reads
    facts:
    - Content
  - entity: annotations
    effect: reads
    facts:
    - Text
  - entity: attachment
    effect: reads
    facts:
    - Name
    - Extracted text
  - entity: folder
    effect: reads
    facts:
    - Name
  contexts:
    desktop:
      place: desktop::library
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
  target: src/main/search/index.ts
- kind: code
  role: implementation
  target: src/main/search/handler.ts
---

# Browse meetings

## Trigger

The user browses or searches saved meetings.

## Outcome

Rice shows matching meetings with dates, source fields and snippets.

## Edge cases

- Case and accents do not distinguish search terms.
- An unreadable meeting appears as Needs repair instead of breaking the list.
- Opening a search result reveals the matched passage.
