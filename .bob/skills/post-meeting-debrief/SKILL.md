---
name: post-meeting-debrief
description: Capture and structure post-meeting notes into a session record. Extracts commitments, open questions, and signals. Scores seller performance against coaching dimensions. Combines Scribe and Coach principles. Use when the seller wants to debrief a meeting, capture session notes, log a session, or process raw meeting notes into structured memory.
---

# Post-Meeting Debrief

You are running the Post-Meeting Debrief skill. This skill combines Scribe and Coach principles to convert raw meeting notes into structured session records.

## Files to Load

1. `memory/seller/IDENTITY.md`
2. `memory/seller/profile.yaml` — for coaching dimensions
3. `memory/clients/[slug]/account.yaml` — engagement tier
4. `memory/clients/[slug]/sessions.yaml` — for context with prior sessions
5. `memory/clients/[slug]/context-stakeholders.md` if available
6. `memory/clients/[slug]/ENGAGEMENT.md` — to update if commitments shift the hypothesis

## Required Input

The seller provides raw meeting notes. If not provided, ask for them. Include:
- Date and meeting type
- Attendees (seller-side and client-side)
- Raw notes / observations

## Output Structure

### Part 1 — Structured Session Record (Scribe principles)

Produce a session record following the sessions.yaml schema:

```
SESSION RECORD — [Client] — [Date]
Type: [meeting type]
Attendees:
  Seller side: [names]
  Client side: [names with titles]
Duration: [if known]

DISCUSSION SUMMARY
[2-4 sentences capturing substance]

SAID (direct attribution)
- [Name]: "[quote or close paraphrase]" — paraphrased: [true/false]

INFERRED (your analysis)
- [Inference with reasoning grounded in observed evidence]

AGREED (commitments — owner + due date required)
- Action: [specific action]
  Owner: [name]
  Due date: [date]

OPEN QUESTIONS
- [Question]
  Needs answer from: [name or role]

SIGNALS TO SURFACE (route to signal-ingestion review)
- [New intelligence worth adding to memory]
```

### Part 2 — Coach Scorecard (Coach principles)

Score the session against the coaching dimensions defined in `profile.yaml`. Use evidence from the session notes — not impressions.

```
COACH SCORECARD — [Client] — [Date]
SELLER-ONLY — NOT FOR CLIENT SHARING

[Dimension]: [Score]/5 — Evidence: [specific moment from notes]
[Dimension]: [Score]/5 — Evidence: [specific moment from notes]
[...]

Strongest moment: [specific observation]
Weakest moment: [specific observation]
One development action before next session: [specific and actionable]
```

### Part 3 — Proposed Memory Updates

Format all proposed writes per the memory protocol:
- New session record for `sessions.yaml`
- Updated commitments status if prior commitments are now complete
- Signals to surface to `signal-ingestion` for review
- Engagement hypothesis update if the session meaningfully shifts it

## Specialist Principles Applied

**Scribe:** Never mix Said / Inferred / Agreed. Commitments require owner and due date. Open questions require who must answer.

**Coach:** Score from evidence in the session notes. No impressionistic scoring. Trends require 3+ sessions before pattern claims.

## Output Labeling

The Scribe portion may include both client-facing and seller-only elements. The Coach scorecard is always `SELLER-ONLY — INTERNAL`.

If the seller needs a follow-up email draft for client sharing, that is a separate `CLIENT-FACING` output with portfolio firewall applied.
