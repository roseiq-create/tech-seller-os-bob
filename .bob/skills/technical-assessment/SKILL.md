---
name: technical-assessment
description: Produce a structured current state landscape assessment with maturity scoring across all configured dimensions. Reads client landscape data and signals, scores each dimension with rationale citing specific evidence, identifies gaps between current and target state. Applies Architect principles. Use when the seller asks to assess a client's current state, run a landscape assessment, score maturity, or produce a technical baseline.
---

# Technical Assessment

You are running the Technical Assessment skill. This is the technical analysis function — it makes the seller credible in front of CTO, CISO, and engineering leadership. Applies Architect principles.

## Files to Load

1. `memory/seller/IDENTITY.md`
2. `memory/seller/profile.yaml` — for configured maturity dimensions
3. `memory/clients/[slug]/account.yaml`
4. `memory/clients/[slug]/client.yaml` — landscape data and existing maturity scores
5. `memory/industries/[industry-slug]/maturity-benchmarks.md` if available

## Output Structure

### Current State Landscape Summary

For each domain configured in `profile.yaml`:
- Components documented (specific to this client)
- Integration patterns observed
- Known constraints (cite signals or session evidence)
- Technical debt indicators

Lead with the finding. Do not summarize what is in client.yaml — extract what matters.

### Maturity Scorecard

For each dimension configured in `profile.yaml.maturity_dimensions`:

```
DIMENSION: [Domain Name]
Current Score: [1-5] / 5
Rationale: [2-3 sentences citing specific evidence from signals or landscape — not generic]
Target Score: [1-5] / 5 (from client.yaml if documented, or "Target needed" if not)
Gap: [What specifically needs to change]
Key Dependencies: [What has to happen before the target is achievable]
Evidence Sources: [client.yaml landscape section, specific signals]
```

Scoring scale:
- 1 — Initial: Ad hoc, undocumented, high variability
- 2 — Developing: Awareness exists, some structure emerging
- 3 — Defined: Documented, repeatable, measurable
- 4 — Managed: Proactively monitored, continuous improvement
- 5 — Optimized: Industry-leading, systematically improving

### Critical Gaps

Identify the gaps between current and target state that:
- Block the highest-impact use cases
- Have the longest dependency chains
- Connect to active client forcing functions (regulatory deadlines, contract decisions, board commitments)

### Prerequisite Map

For each significant gap, identify what must be in place first. Be explicit about technical dependencies — do not assume the seller knows them.

### Honest Gap Disclosure

If landscape data is incomplete or maturity scoring is not possible due to missing evidence, say so. Do not invent scores. Use "Score not yet possible — evidence needed: [what specifically]".

## Specialist Principles Applied

**Architect:** Evidence-based. Every score cites specific evidence. Use cases linked to client priorities. Roadmap sequencing respects technical prerequisites. Maturity dimensions are configured in profile.yaml — never use generic defaults.

## Output Labeling

The assessment itself is typically `CLIENT-FACING` (suitable for sharing with the client's technology leadership), but apply the portfolio firewall — no portfolio vendor names appear in the output unless the client has documented them in their landscape.

If the assessment includes seller-only strategic implications, produce two versions: a client-facing assessment and a seller-only strategic interpretation.

## Memory Write Discipline

The Technical Assessment may propose updates to:
- `client.yaml.maturity` — new or updated scores with rationale
- `client.yaml.landscape` — additions to documented landscape
- `ENGAGEMENT.md` — engagement hypothesis update if findings shift it

All writes follow the confirmation gate.

## Follow-On Skills

After Technical Assessment, the natural next skills are:
- `use-case-generation` — generate specific opportunities from the gaps
- `roadmap-sequencing` — sequence use cases respecting prerequisites
- `architecture-diagrams` — visualize current and target states

Suggest these explicitly when handing off.
