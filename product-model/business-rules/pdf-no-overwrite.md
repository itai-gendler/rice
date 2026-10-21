---
appliesTo:
- type: capability
  id: export-meeting-pdf
- type: capability
  id: export-privacy-receipt
references:
- kind: code
  role: implementation
  target: src/main/share/pdf.ts
- kind: code
  role: implementation
  target: src/main/app/main.ts#shareDeps
---

# PDF exports do not overwrite existing files

Exports use the current meeting text, the supplied name or a title-derived default, and a suffixed available filename in the remembered destination.
