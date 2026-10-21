---
appliesTo:
- type: entity
  id: folder
- type: entity
  id: settings
- type: entity
  id: privacy-receipt
references:
- kind: code
  role: implementation
  target: src/main/privacy/folder-rules.ts
- kind: code
  role: implementation
  target: src/main/ai/factory.ts
- kind: code
  role: implementation
  target: src/main/privacy/redact.ts
---

# Sensitive folders inherit text redaction

The global personal-data choice or sensitivity on any ancestor folder requests redaction for remote AI text. Supported recognized personal data is replaced with per-call markers and restored in the answer locally. Images are omitted from such calls. Local-model calls stay local.
