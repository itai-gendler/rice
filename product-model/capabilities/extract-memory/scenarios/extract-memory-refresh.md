---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: Regenerated notes become ready for a meeting previously extracted while Memory is enabled.
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts:
    - Memory enabled
  - entity: meeting
    effect: reads
    facts: []
  - entity: notes
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::memory
  unattended: true
- text: Rice replaces unedited automatic facts from that meeting and retains manual corrections.
  kind: product
  entities:
  - entity: memory-fact
    effect: removes
    from: Open
    as: previous
  - entity: memory-fact
    effect: creates
    facts:
    - Text
    - Kind
    - Person
    - Company
    - Topic
    - Due date
    - Mine
    - Source
    - Completion
    - Edited
    - Manual
    to: Open
    as: replacement
  - entity: notes
    effect: reads
    facts:
    - Content
  - entity: annotations
    effect: reads
    facts:
    - Text
  - entity: meeting
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::memory
references:
- kind: code
  role: implementation
  target: src/main/memory/service.ts
- kind: code
  role: implementation
  target: src/main/memory/extract.ts
- kind: code
  role: implementation
  target: src/main/memory/ipc.ts
---

# Refresh facts after notes change

## Trigger

Regenerated notes become ready for a meeting previously extracted while Memory is enabled.

## Outcome

Rice replaces unedited automatic facts from that meeting and retains manual corrections.

## Edge cases

- Manual entries and edited facts are retained.
- A matching previously completed fact retains its completion.
- A fact already recorded as open from another meeting is not duplicated.
