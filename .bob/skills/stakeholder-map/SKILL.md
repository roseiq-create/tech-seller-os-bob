---
name: stakeholder-map
description: Build or update structured map of decision authority, influence patterns, ally and blocker classifications, and relationship momentum for an active client engagement. SELLER-ONLY workflow — outputs are never shared with clients under any circumstances. Use when the seller asks to map stakeholders, run a stakeholder analysis, build a political map, or assess decision authority and relationship dynamics for a client.
---

# Stakeholder Map

You are running the Stakeholder Map skill. **SELLER-ONLY MODE.** Nothing produced by this skill is ever shared with clients.

## Files to Load

1. `memory/seller/IDENTITY.md`
2. `memory/clients/[slug]/account.yaml` — contact roster
3. `memory/clients/[slug]/sessions.yaml` — for observed behavior and quotes
4. `memory/clients/[slug]/stakeholder-map.yaml` — existing map if any
5. `memory/clients/[slug]/ENGAGEMENT.md` — engagement context

## Stakeholder Dimensions

Score each stakeholder across five dimensions:

**Decision authority:**
- Final — Signs off, can unilaterally approve or kill
- Strong influence — CxO peer input that moves the final decision
- Advisory — Consulted but not decisive
- Blocking power — Can stop but cannot approve

**Relationship warmth:**
- Champion — Actively advocating for the seller's success
- Supportive — Positive, engaged, not yet championing
- Neutral — No strong lean
- Skeptical — Doubts but open to being convinced
- Blocker — Actively working against

**Engagement momentum:**
- Deepening — More access, more candor, growing trust
- Stable — Consistent engagement, no regression
- Cooling — Less access, shorter responses, reduced candor
- At risk — Significant regression requiring active attention

**Technical depth:**
- Strategic — Cares about outcomes and business case
- Hands-on — Engages on architecture and implementation detail
- Non-technical — Needs translation from technical to business language

**Reachability:**
- Direct — Seller has direct relationship
- Through ally — Only accessible via a champion or intermediary
- Indirect — No current path; relationship does not exist yet

## Output Structure

```
STAKEHOLDER MAP — [Client] — [Date]
SELLER-ONLY — NOT FOR CLIENT SHARING

[Stakeholder Name] — [Title]
Decision authority: [tier]
Relationship warmth: [tier]
Engagement momentum: [tier]
Technical depth: [tier]
Reachability: [tier]

Key insight: [What you know about this person that is not obvious — grounded in observed behavior, not assumption]
Primary concern: [What they actually care about — their agenda, not the stated agenda]
Preferred communication: [How they engage best — observed from sessions]

Relationship history: [How the relationship has evolved]
Last meaningful interaction: [Date and what happened]

Risk in meeting: [What could go wrong with this person in the room]
Recommended next move: [Specific next relationship action]

Through ally: [If reachability = Through ally, name the ally]

EVIDENCE SOURCES: [Specific session references, quoted observations]

---

[Next stakeholder...]

---

VISIBILITY GAPS
[Roles or stakeholders where you have no relationship and that creates risk]
- Role: [e.g., CFO]
  Risk: [Why this matters for the engagement]
  Path to access: [Recommended approach]

POLITICAL DYNAMICS
[Coalitions, tensions, conflicts between stakeholders affecting the deal]
- Dynamic: [Description]
  Impact: [How this affects engagement strategy]
  Evidence: [What was observed that supports this]
```

## Honesty Requirement — No Speculation Without Evidence

Never speculate about motivations, alliances, or political dynamics without citing evidence from session notes. If you do not have evidence, flag it:

```
HYPOTHESIS — NEEDS VALIDATION
[Stakeholder X may have political tension with Y based on (limited indirect signal)]
What to watch for: [Specific behavior that would confirm or deny]
```

The seller's map is only as good as the evidence in it. Fabricated political intelligence is worse than no intelligence.

## Specialist Principles Applied

**Stakeholder Map agent:** SELLER-ONLY. Work from observed behavior, not assumption. Flag gaps explicitly. Never share with clients under any circumstances.

## Output Labeling

`SELLER-ONLY — NOT FOR CLIENT SHARING` at the top of every output. This labeling is mandatory and is the highest enforcement priority — if any output from this skill leaks into client-facing material, it is a serious operating principle violation.

## Memory Write Discipline

Propose updates to `memory/clients/[slug]/stakeholder-map.yaml`. This file is the most politically sensitive in the entire system. Every write goes through explicit confirmation.

## Pre-Meeting Integration

The `pre-meeting-cockpit` skill reads `stakeholder-map.yaml` to inform meeting preparation. Keep this file current — outdated stakeholder maps create blind spots in high-stakes meetings.
