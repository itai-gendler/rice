---
appliesTo:
- type: entity
  id: finding
references:
- kind: code
  role: implementation
  target: src/main/warroom/store.ts#contextFacts
---

# Pinned findings are prioritized within a bounded context

Visible pinned findings precede up to twelve recent unpinned findings, within the context character budget. Dismissed findings are excluded. Pinning does not make an unlimited number of findings fit.
