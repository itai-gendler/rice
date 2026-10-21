---
appliesTo:
- type: entity
  id: memory-fact
  effect: removes
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
permits:
- actors:
  - user
- unattended: true
  when:
  - entity: settings
    fact: Memory enabled
    is: true
---

# The user removes facts and Rice replaces automatic extraction

The user can delete facts directly or by removing their source meeting, forgetting a person or company, or erasing Memory. With Memory enabled, re-extraction replaces earlier unedited automatic facts from that source.
