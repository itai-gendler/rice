---
appliesTo:
- type: capability
  id: draft-follow-up-email
- type: capability
  id: copy-email-draft
- type: capability
  id: open-email-draft
references:
- kind: code
  role: implementation
  target: src/main/share/actions.ts
- kind: code
  role: implementation
  target: src/main/share/mailto.ts
---

# Email drafts are handed to the person to send

Rice generates editable text and opens Mail or copies it; it does not send email. A mail link over 8,000 characters is refused with Copy still available.
