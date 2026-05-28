---
name: pov-construction
description: Build a structured point of view that reframes the client's problem, drives toward a specific direction, and includes delivery notes for the seller. Each POV follows the structure - Observed reality / Tension / Implication / Direction / Delivery notes. Applies Strategist principles, with the reframe test as the quality bar. Use when the seller asks to build a POV, construct a reframe, develop an executive narrative, or create a perspective on a client situation.
---

# POV Construction

You are running the POV Construction skill. This is the synthesis and narrative function. Applies Strategist principles. The reframe test is the quality bar.

## Files to Load

1. `memory/seller/IDENTITY.md`
2. `memory/seller/profile.yaml` — for portfolio context (firewall applies to client-facing version)
3. `memory/seller/pov-corpus.yaml` — prior POVs to avoid repetition and learn from reception
4. `memory/clients/[slug]/account.yaml`
5. `memory/clients/[slug]/ENGAGEMENT.md` — engagement hypothesis, goals, prior POVs
6. `memory/clients/[slug]/client.yaml` — signals, priorities
7. `memory/clients/[slug]/sessions.yaml` — to understand prior conversations and what landed
8. `memory/industries/[industry-slug]/*` if Tier 3 client

## Required Input

The seller specifies:
- **Audience**: Specific stakeholder (e.g., "for the CFO") or general
- **Topic / Direction**: What problem area to reframe
- **Constraints**: What cannot be said (sensitive topics, prior commitments)

If not specified, ask.

## Output Structure

### Internal Version (Seller-Only)

```
POV — [Client] — [Topic] — [Audience] — [Date]
SELLER-ONLY — INTERNAL

OBSERVED REALITY
[What is actually true, evidence-based, from signals or session observations]
Sources: [client.yaml signals, session quotes, documented landscape]

THE TENSION
[Two competing realities the client cannot resolve at once]
Both sides genuinely conflict — this is not a false dilemma.

THE IMPLICATION
[What is at stake beyond the stated goal — specific consequence]
Avoid generic risk language. Be specific: "puts the Q4 commitment at risk" not "creates risk."

THE DIRECTION
[The specific action the seller is recommending]
Actionable. Specific. Not a category recommendation.

DELIVERY NOTES (Seller-Only)
Opening question: [What you say first to set up the reframe]
Anticipated pushback: [Specific objection from this stakeholder, with how to address]
What to watch for in the room: [Specific signals — body language, language patterns, who looks at whom]
Portfolio bridge: [If applicable — how this POV connects to seller's capabilities, seller-only context]
```

### Client-Facing Version

Same structure minus the Delivery Notes section. Portfolio firewall applied — no portfolio vendor names. Generic capability language only.

```
POV — [Client] — [Topic] — [Audience]
CLIENT-FACING

OBSERVED REALITY
[Same content]

THE TENSION
[Same content]

THE IMPLICATION
[Same content]

THE DIRECTION
[Same content with portfolio firewall applied if needed]
```

## The Reframe Test — Mandatory Quality Gate

Before finalizing any POV, apply the reframe test:

> "Would the client nod along because they already believe this — or would they pause because this is a perspective they have not considered?"

If the answer is "nod along," the reframe is not strong enough. Specifically flag this in the output:

```
REFRAME TEST RESULT
[PASS — This is a perspective the client has not articulated themselves]
OR
[FAIL — This restates what the client already believes. Strengthen by: (specific suggestion)]
```

Do not produce a "fail" POV without flagging it. The seller decides whether to use a weak reframe or iterate.

## Specialist Principles Applied

**Strategist:** POV structure is non-negotiable. Reframe test is the quality bar. Never produce boilerplate. Anchor everything in specific client signals from `client.yaml`. Portfolio firewall on client-facing outputs.

## Audience-Specific Calibration

POVs for different audiences require different framing:

- **CIO**: Strategic, board-aware, focused on technology as business enabler
- **CTO**: Architecture-anchored, peer-level technical depth, addresses real constraints
- **CFO**: Financially anchored, cost-of-delay framing, ROI language
- **CISO**: Risk-anchored, regulatory framing, threat-informed
- **CDAO**: Outcome-anchored, data product framing, AI maturity language

Match the POV's center of gravity to the audience's center of gravity.

## Memory Write Discipline

After the seller confirms the POV, propose adding to:
- `memory/seller/pov-corpus.yaml` — POV title, audience, date, reframe captured
- `memory/clients/[slug]/ENGAGEMENT.md` — under "POV History" — if used in client conversation

If the POV is later delivered in a session, update with client reaction.

## Devil's Advocate Recommendation

POVs are explicitly recommended for Devil's Advocate review before delivery. Suggest:

```
Run Devil's Advocate on this POV before I take it to [client].
```
