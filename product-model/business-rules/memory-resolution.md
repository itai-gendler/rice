---
appliesTo:
- type: entity
  id: memory-fact
  effect: changes
  to: Done
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

# The user completes follow-ups and Rice resolves them from later notes with Memory enabled

Automatic resolution names the later completing meeting and applies to an earlier open commitment or request. The user can reopen it.
