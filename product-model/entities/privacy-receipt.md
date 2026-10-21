---
references:
- kind: code
  role: implementation
  target: src/main/privacy/egress.ts
- kind: code
  role: implementation
  target: src/renderer/receipt-card.js
---

# Privacy receipt

The user-visible record of AI use for one meeting.

## Information kept

- **Activity** — Time, purpose, provider, local or remote route and input sizes for each recorded call.
- **Summary** — Grouped send counts and latest times, image counts, web use and redaction counts.
- **Consent** — The recorded time the notice was copied.
- **Microphone** — The device name and changes shown with the receipt.
