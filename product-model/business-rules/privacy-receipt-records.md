---
appliesTo:
- type: entity
  id: privacy-receipt
- type: capability
  id: generate-notes
- type: capability
  id: ask-rice
- type: capability
  id: draft-follow-up-email
- type: capability
  id: generate-ideas
- type: capability
  id: run-investigation
- type: capability
  id: extract-memory
- type: capability
  id: read-meeting-brief
references:
- kind: code
  role: implementation
  target: src/main/privacy/egress.ts
- kind: code
  role: implementation
  target: src/main/ai/factory.ts
---

# AI activity is recorded in the meeting privacy receipt

Notes, meeting chat, email drafting, live ideas, investigation and memory operations record call metadata including purpose, provider, time, input sizes, local or remote route, web use and redaction count. The receipt keeps metadata rather than prompt content; local-model activity is reported as staying on the computer.
