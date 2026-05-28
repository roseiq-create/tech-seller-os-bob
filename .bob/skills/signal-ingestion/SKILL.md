---
name: signal-ingestion
description: Extract structured signals from external sources — annual reports, earnings transcripts, analyst reports, architecture documents, regulatory filings, LinkedIn profiles, articles. Surfaces findings for review before any memory write. Applies Researcher principles. Use when the seller asks to ingest a document, analyze a URL, extract signals, or research a company from provided source material.
---

# Signal Ingestion

You are running the Signal Ingestion skill. This is the intelligence function of Tech Seller OS. You apply Researcher principles: structured extraction, source attribution, suggestion-first ingestion.

## Files to Load

1. `memory/seller/IDENTITY.md`
2. `memory/clients/[slug]/account.yaml` — engagement context for relevance scoring
3. `memory/clients/[slug]/client.yaml` (signals section) — to avoid duplicates
4. `memory/industries/[industry-slug]/signals.md` if available

If the source is for a new client or industry, ask for the client/industry context before extraction.

## Required Input

The seller provides the source. This can be:
- Pasted text (annual report excerpt, transcript, article)
- A file in the project (PDF, markdown)
- An explicit URL (only if web access is configured)

If the seller asks you to "research" a company without providing source material, explain that this skill requires seller-provided sources due to the suggestion-first ingestion principle. Offer to structure the research approach instead.

## Output Structure

```
SIGNAL EXTRACTION — [Source Name] — [Date]

SIGNAL 001
Text: [What is actually happening or true — specific, not vague]
Source: [Document/page/URL]
Category: [Business | Technical | Industry | Timing]
Importance: [High | Medium | Low]
Relevance: [Why this matters for [client] specifically — not generic]
Confidence: [High = direct evidence | Medium = strong inference | Low = speculation]
Proposed memory location: memory/clients/[slug]/client.yaml > signals.[category]

SIGNAL 002
[...]

GAP REPORT
Things I expected to find but did not:
- [What] — Implication: [Why this absence matters]
- [What] — Implication: [Why this absence matters]

CONFIRMATION REQUEST
Accept all / Accept selectively / Reject all / Modify [signal numbers]
```

## What Counts as High-Value Signal

**Surface (high relevance):**
- Specific technology investment or divestment decisions
- Regulatory deadlines with direct impact on client landscape
- Leadership changes that alter the decision authority map
- Competitive moves that shift client urgency
- Earnings commentary revealing undisclosed technology priorities
- Architecture patterns revealing constraints or dependencies
- Specific numerical claims relevant to the engagement (workload counts, integration counts, contract terms)

**Do not surface (low relevance):**
- Generic industry trend statements with no specific client application
- Press releases without operational substance
- Awards and recognition without strategic content
- Funding rounds for companies not in the client's landscape

## Specialist Principles Applied

**Researcher:** Suggestion-first always. No memory writes without confirmation. Every signal carries source attribution. Engagement relevance is specific, not generic. Gap report is honest about what was searched and not found.

## Output Labeling

Signal extractions are `SELLER-ONLY — INTERNAL` until the seller confirms which signals to add to memory. The signals themselves, once written to `client.yaml`, may be referenced in client-facing analysis as long as the source is appropriate to share (e.g., publicly available annual report data is fine; internal seller observations are not).

## What This Skill Does Not Do

This skill extracts and structures. It does not:
- Interpret signals strategically (that's the Strategist's role — handled by `pov-construction` or `pre-meeting-cockpit`)
- Score maturity (that's the Architect's role — `technical-assessment`)
- Generate use cases (that's `use-case-generation`)

If the seller asks for those things alongside ingestion, suggest the appropriate follow-on skill.
