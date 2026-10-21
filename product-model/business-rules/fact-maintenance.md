---
appliesTo:
- type: entity
  id: memory-fact
  effect: changes
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

# The user edits remembered facts and Rice maintains them when Memory is enabled

The user can correct or reopen stored facts and set follow-up due dates. Automatic maintenance requires Memory enabled.
