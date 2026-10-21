---
appliesTo:
- type: entity
  id: attachment
references:
- kind: code
  role: implementation
  target: src/main/attachments/store.ts
---

# Attachments respect per-file and per-meeting size limits

Each file is at most 50 MiB and all attachments for one meeting total at most 500 MiB. Filename conflicts receive a suffix. Supported extracted text contributes to search and AI context; lack of PDF extraction does not prevent local attachment storage.
