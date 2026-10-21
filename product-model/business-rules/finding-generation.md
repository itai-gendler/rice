---
appliesTo:
- type: entity
  id: finding
  effect: creates
references:
- kind: code
  role: implementation
  target: src/main/warroom/ipc.ts
- kind: code
  role: implementation
  target: src/main/warroom/engine.ts
- kind: code
  role: implementation
  target: src/renderer/warroom.js
permits:
- actors:
  - user
  when:
  - entity: meeting
    fact: Investigation active
    is: true
  - entity: meeting
    fact: Capture running
    is: true
  - entity: meeting
    fact: Cycle ceiling
    is: 0
- actors:
  - user
  when:
  - entity: meeting
    fact: Investigation active
    is: true
  - entity: meeting
    fact: Capture running
    is: true
  - entity: meeting
    fact: Investigation count
    under:
      entity: meeting
      fact: Cycle ceiling
- unattended: true
  when:
  - entity: meeting
    fact: Investigation active
    is: true
  - entity: meeting
    fact: Capture running
    is: true
  - entity: meeting
    fact: Cycle ceiling
    is: 0
- unattended: true
  when:
  - entity: meeting
    fact: Investigation active
    is: true
  - entity: meeting
    fact: Capture running
    is: true
  - entity: meeting
    fact: Investigation count
    under:
      entity: meeting
      fact: Cycle ceiling
---

# The user and Rice generate findings only while their track is active

Manual and scheduled live generation require unpaused capture, the corresponding enabled track and remaining cycles. A zero ceiling means unlimited.
