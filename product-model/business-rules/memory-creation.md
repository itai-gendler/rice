---
appliesTo:
- type: entity
  id: memory-fact
  effect: creates
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

# The user adds facts and Rice extracts them only with Memory enabled

Manual follow-ups are user-entered facts. Automatic extraction runs from ready notes only while Memory is enabled.
