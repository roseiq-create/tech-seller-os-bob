---
name: roadmap-sequencing
description: Sequence client use cases into a three-horizon roadmap (NOW / NEAR / STRATEGIC) respecting technical prerequisites and forcing functions. Flags dependency conflicts and missing prerequisites. Applies Architect principles. Use when the seller asks to sequence a roadmap, build a horizon plan, organize use cases by timing, or produce a multi-year technology plan.
---

# Roadmap Sequencing

You are running the Roadmap Sequencing skill. Applies Architect principles. Output is a three-horizon roadmap grounded in technical dependencies.

## Files to Load

1. `memory/seller/IDENTITY.md`
2. `memory/seller/profile.yaml`
3. `memory/clients/[slug]/account.yaml`
4. `memory/clients/[slug]/client.yaml` — all use cases, landscape, maturity scores
5. `memory/clients/[slug]/ENGAGEMENT.md` — forcing functions, board commitments, decision deadlines

## Horizon Definitions

- **NOW (0-6 months)**: Foundation work, no-regret moves, quick wins, regulatory deadlines
- **NEAR (6-18 months)**: Strategic capability development, platform enablement
- **STRATEGIC (18-36 months)**: Transformational outcomes, business value realization

## Output Structure

### Horizon 1: NOW
Table of use cases placed in this horizon. For each:
- Use case ID and title
- Domain
- Impact / Feasibility scores
- Prerequisites status (met / blocked / partial)
- Forcing function driving the timing

### Horizon 2: NEAR
Same structure.

### Horizon 3: STRATEGIC
Same structure.

### Critical Path Analysis

Identify the longest dependency chain. State explicitly:
- Critical path use cases in sequence
- Total critical path duration
- Single points of failure (what kills the whole path if it slips)

### Parallel Paths

Use cases that can execute concurrently:
- Group by which use cases share no dependencies
- Identify which can be deployed in parallel teams

### Dependency Conflicts and Flags

If any use case is placed in a horizon before its prerequisites complete in an earlier horizon, flag it explicitly:

```
DEPENDENCY CONFLICT
Use case: [ID and title]
Placed in: [Horizon]
Required prerequisite: [Use case ID]
Prerequisite placement: [Horizon — same or later, which causes the conflict]
Resolution options:
- Move prerequisite earlier
- Move dependent use case later
- Accept partial implementation
```

### Forcing Function Alignment

For each horizon, name the external forcing functions driving the timeline:
- Regulatory deadlines
- Contract renewal windows
- Board commitments
- Budget planning cycles
- Competitive pressure events

If a forcing function requires a use case to complete by a date that the dependency chain cannot meet, flag it as a **timeline conflict** explicitly:

```
TIMELINE CONFLICT
Forcing function: [Specific event/date]
Required completion: [Use case ID by date]
Earliest feasible completion: [Date based on dependencies]
Gap: [Months/quarters]
Implications: [What this means for the engagement]
Options: [Faster path with narrower scope, accept delay, reset expectation]
```

### Maturity Progression by Horizon

For each maturity dimension in `profile.yaml.maturity_dimensions`, show projected progression:
- Current score (from `client.yaml.maturity`)
- Horizon 1 projected score
- Horizon 2 projected score
- Horizon 3 projected score
- Direct vs. Indirect impact noted

Be honest about dimensions that do not move (e.g., Developer Experience may stay at 1/5 in Horizon 1 because dependencies are not yet in place).

### Investment Sequencing Logic

Explain why this sequence — not just what it is. For each horizon, articulate:
- Why these use cases in this horizon
- What dependencies drove the placement
- What was deliberately not placed here and why

### Business Case Structure (NOT Numbers)

Provide a structure for investment sizing, but do **NOT** fabricate dollar amounts. If cost source data does not exist in memory, label every line:

```
HORIZON 1 INVESTMENT
[Use case]: [Estimate — source needed: cost modeling required]
[Use case]: [Estimate — source needed: cost modeling required]

Total Horizon 1: [Estimate — source needed]
```

The seller populates the numbers from real cost modeling. Never invent them.

## Specialist Principles Applied

**Architect:** Sequence respects technical prerequisites — no aspiration timelines. Conflicts are flagged explicitly. Maturity progression is honest about lag effects. Investment structure exists; numbers come from source data only.

## Output Labeling

Default `SELLER-ONLY — INTERNAL` because roadmap typically includes portfolio bridging considerations. When the seller wants a `CLIENT-FACING` version, produce one with portfolio firewall applied and seller-only sections removed.

## Memory Write Discipline

Roadmap sequencing may propose updates to:
- `client.yaml.use_cases` — time_horizon field for each use case
- `client.yaml.roadmap` — new section with horizon placement
- `ENGAGEMENT.md` — if roadmap reveals timeline conflicts with engagement hypothesis

All writes follow the confirmation gate.

## Devil's Advocate Recommendation

For roadmap deliverables going to board or CFO audiences, explicitly recommend Devil's Advocate review:

```
Run Devil's Advocate on the roadmap before [meeting].
```

Especially valuable when timeline conflicts exist — Devil's Advocate will challenge whether the political narrative is viable.
