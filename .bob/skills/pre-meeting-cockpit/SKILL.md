---
name: pre-meeting-cockpit
description: Prepare for an upcoming client meeting. Reads seller identity, client memory files, and recent sessions to produce a structured pre-meeting intelligence brief with meeting purpose, intelligence gaps, research questions, and strategic objective. Combines Researcher and Strategist principles. Use when the seller mentions an upcoming client meeting, asks for meeting prep, or needs to build a meeting brief.
---

# Pre-Meeting Cockpit

You are running the Pre-Meeting Cockpit skill. This skill combines Researcher and Strategist principles to produce a structured pre-meeting intelligence brief.

## Files to Load

Before producing output, load:
1. `memory/seller/IDENTITY.md` — seller identity and operating principles
2. `memory/clients/[slug]/account.yaml` — first read to determine engagement tier
3. Based on tier:
   - Tier 2+: `memory/clients/[slug]/ENGAGEMENT.md`, `client.yaml`, `sessions.yaml`
   - Tier 2+: `memory/clients/[slug]/stakeholder-map.yaml` (seller-only — for political context)
   - Tier 3: `memory/industries/[industry-slug]/*` if available

If the client slug is not provided, ask which client.

## Output Structure

Produce a single intelligence brief with these sections:

### 1. Engagement Context Header
- Tier, relationship status, engagement health
- Last session date and elapsed time
- Next planned touchpoint

### 2. Most Likely Meeting Purpose & Audience
- Primary purpose with reasoning
- Expected audience based on session history
- Why this timing matters (forcing functions, commitments)

### 3. Intelligence Gaps to Close
For each gap:
- Why it matters (specific to the engagement)
- Current state (what is known)
- Risk level: HIGH | MEDIUM | LOW
- Action to close the gap

### 4. Specific Research Questions & Sources
For each question:
- Specific sources to check
- What to look for
- Apply suggestion-first ingestion — do not pretend to have done external research you cannot do

### 5. Strategic Objective for the Session
- Primary objective (one sentence)
- Success criteria (3-5 specific outcomes)
- Conversation framing strategy (Open / Middle / Close)
- What to avoid (specific failure modes from session history)
- Stakeholder-specific approach (one paragraph per likely attendee)

### 6. Recommended Pre-Meeting Actions
- Priority 1 (Must Complete)
- Priority 2 (Should Complete)
- Priority 3 (Nice to Have)

## Specialist Principles Applied

**Researcher principles:** Gap report discipline. Every gap has source attribution and engagement relevance. Cannot do external research without explicit sources provided by the seller.

**Strategist principles:** Conversation framing applies the reframe test. Stakeholder-specific approaches reference what is known from session history, not assumed.

## Output Labeling

This skill produces `SELLER-ONLY — INTERNAL` output. The brief contains stakeholder political intelligence and is not for client sharing.

## Devil's Advocate

For high-stakes meetings (board-attended, decision-forcing, EBR), the seller should run Devil's Advocate as a follow-up:
```
Run Devil's Advocate on the Pre-Meeting Cockpit output for [client].
```

Do not auto-fire Devil's Advocate — let the seller decide.

## Memory Write Discipline

This skill does not propose memory writes by default. Findings are surfaced for the seller's preparation. If the seller asks to update specific files (e.g., "add the CFO question to the engagement open questions"), propose a structured update per the memory protocol.
