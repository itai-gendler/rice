---
references:
- kind: code
  role: implementation
  target: src/shared/types.ts
- kind: code
  role: implementation
  target: src/main/session/meeting-session.ts
- kind: code
  role: implementation
  target: src/main/warroom/store.ts
relations:
- entity: transcript
  verb: has
  cardinality: one-to-one
- entity: annotations
  verb: has
  cardinality: one-to-one
- entity: notes
  verb: has
  cardinality: one-to-one
- entity: notes-version
  verb: keeps
  cardinality: one-to-many
- entity: meeting-chat
  verb: has
  cardinality: one-to-one
- entity: attachment
  verb: contains
  cardinality: one-to-many
- entity: screenshot
  verb: contains
  cardinality: one-to-many
- entity: idea
  verb: receives
  cardinality: one-to-many
- entity: finding
  verb: receives
  cardinality: one-to-many
- entity: privacy-receipt
  verb: has
  cardinality: one-to-one
---

# Meeting

A saved meeting, including its recording history and choices for future note generation.

## Information kept

- **Title** — The editable name.
- **Date** — Creation or first recording time and latest end time.
- **Sessions** — The recording stretches belonging to this meeting.
- **Capture in use** — Whether this meeting holds the one active recording, paused or not; it is released as soon as recording stops, before finishing completes.
- **Capture running** — Whether audio is being captured right now: recording and not paused.
- **Ideas enabled** — Whether suggestions are enabled for this meeting.
- **Investigation active** — Whether War room investigation is enabled and its track is not paused.
- **Language** — Portuguese, English or Automatic; absent selection uses the default.
- **Template** — The note template selected for the next generation.
- **Folder** — The optional organizational folder.
- **Participants** — Calendar participant names and recipient addresses, when supplied.
- **Speaker names** — Names assigned to identified voices in this meeting.
- **Audio** — Whether saved audio is available and the recording stretches it contains.
- **Microphone** — The input name and changes during recording.
- **Consent copied** — When the recording notice was copied.
- **Calendar event** — The event this meeting prepares or records.
- **Recording alerts** — Current capture, silence, storage or interruption notices.
- **Mode** — Meeting or War room.
- **Ideas settings** — The suggestion interval and selected idea template.
- **Investigation settings** — Interval, paused choice and selected sources.
- **Extra cycles** — Additional live cycles this meeting allows beyond the configured limit, added thirty at a time.
- **Ideas count** — Completed idea cycles for this meeting.
- **Investigation count** — Completed investigation cycles for this meeting.
- **Cycle ceiling** — Effective per-track allowance: the configured limit plus this meeting’s extra cycles, or zero for unlimited.

## States

### Draft

Prepared but not yet recorded.

### Recording

Capturing a recording stretch.

### Paused

An active stretch is deliberately paused and its microphone released.

### Finishing

Capture has ended and remaining transcription and audio are being finalized.

### Done

The recorded material has finished processing; notes may still be generating or need retry.

### Interrupted

An earlier recording did not finish before Rice closed.

### Needs repair

The saved meeting details cannot be read and the list offers repair.
