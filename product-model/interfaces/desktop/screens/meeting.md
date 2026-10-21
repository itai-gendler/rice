---
entities:
- entity: meeting
  shows:
  - Title
  - Date
  - Sessions
  - Capture in use
  - Capture running
  - Ideas enabled
  - Investigation active
  - Language
  - Template
  - Folder
  - Participants
  - Speaker names
  - Audio
  - Microphone
  - Consent copied
  - Calendar event
  - Recording alerts
  - Mode
  - Ideas settings
  - Investigation settings
  - Extra cycles
  - Ideas count
  - Investigation count
  - Cycle ceiling
  collects:
  - Title
  - Language
  - Template
  - Speaker names
  - Ideas settings
  - Investigation settings
- entity: notes
  shows:
  - Content
  - Progress
- entity: transcript
  shows:
  - Content
  - Partial speech
  - Gaps
- entity: annotations
  shows:
  - Text
  collects:
  - Text
- entity: notes-version
  shows:
  - Content
  - Template
  - Date
- entity: attachment
  shows:
  - Name
  - Content
  - Size
  - Kind
  - Added
  - Text availability
- entity: screenshot
  shows:
  - Image
  - Time
  - Caption
  - Trigger
  - Transcript position
- entity: idea
  shows:
  - Text
  - Time
  - Category
  - Template
- entity: finding
  shows:
  - Text
  - Time
  - Source
  - Pinned
- entity: memory-fact
  shows:
  - Text
  - Person
  - Company
  - Due date
  - Source
  - Completion
- entity: note-template
  shows:
  - Title
  - Description
  - Sections
- entity: idea-template
  shows:
  - Title
  - Description
  - Instruction
  - Categories
- entity: privacy-receipt
  shows:
  - Summary
  - Consent
  - Microphone
  - Activity
- entity: settings
  shows:
  - Meetings folder
references:
- kind: code
  role: implementation
  target: src/renderer/renderer.js
---

# Meeting

One meeting and its notes, transcript, annotations, recording controls, attachments, ideas and investigation.
