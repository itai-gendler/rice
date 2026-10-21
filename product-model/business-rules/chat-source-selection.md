---
appliesTo:
- type: entity
  id: all-meetings-chat
references:
- kind: code
  role: implementation
  target: src/main/search/global-chat.ts
- kind: code
  role: implementation
  target: src/main/search/retrieve.ts
---

# Cross-meeting answers retain their selected source links

Retrieval respects the selected folder including descendants and any parsed period. Useful matching terms select at most eight meetings; generic and no-match fallback uses at most five. The no-match fallback is disclosed. Empty periods do not silently widen.
