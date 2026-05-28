---
name: weekly-review
description: Run cross-client territory review. Synthesizes patterns across active engagements, scores relationship health, surfaces decay signals, identifies highest-leverage actions for the coming week. Combines Connector and Coach principles. Use when the seller asks for a weekly review, territory review, cross-client synthesis, or wants to identify priority actions across the portfolio.
---

# Weekly Review

You are running the Weekly Review skill. This is the highest-leverage cross-client workflow in Tech Seller OS. Combines Connector and Coach principles.

## Files to Load

1. `memory/seller/IDENTITY.md`
2. `memory/seller/profile.yaml` — for coaching dimensions and portfolio context
3. All `memory/clients/*/account.yaml` files — for active engagement health
4. All `memory/clients/*/sessions.yaml` files — for recent session momentum
5. All `memory/clients/*/ENGAGEMENT.md` files if Tier 2+
6. `memory/portfolio-alignment/*.yaml` for cross-client portfolio analysis

## Minimum Threshold

The Connector requires at least 2 active clients for meaningful cross-client synthesis. If only 1 client exists, the skill runs in degraded mode — producing single-client health review only and flagging the limitation explicitly.

## Output Structure

```
WEEKLY REVIEW — Week of [date]
SELLER-ONLY — NOT FOR CLIENT SHARING

ACTIVE ENGAGEMENT HEALTH
[Client]: [Deepening | Stable | Cooling | At risk]
  Recent signals: [most recent activity]
  Last session: [date and elapsed time]
  Open commitments: [count, with any overdue flagged]
  Key risk: [if any]

[Client]: [...]

CROSS-CLIENT PATTERNS (Connector — minimum 2 clients required)
Pattern 1: [Description of pattern observed across clients]
  Observed in: [client slugs — not specifics]
  Implication: [what this means for the seller's strategy]
  
Pattern 2: [...]

PORTFOLIO INTELLIGENCE
High-performing use case: [Which use case works across clients]
Stalling use case: [Which use case struggles and why]
Emerging theme: [Pattern across multiple clients suggesting new positioning]

COACHING TRENDS (Coach — minimum 3 sessions for trends)
Strengthening dimension: [Coaching dimension showing improvement, evidence]
Plateauing dimension: [Coaching dimension showing no progress, hypothesis]
Decay signal: [Coaching dimension showing decline, root cause hypothesis]

TERRITORY PRIORITIES — NEXT WEEK
Highest leverage action: [Specific client, specific action, specific outcome]
Relationship requiring attention: [Client and specific risk signal]
Opportunity worth investing in: [Pattern-based opportunity]

GAPS AND VISIBILITY
[Clients where session frequency suggests cooling]
[Stakeholders with no recent contact]
[Open commitments overdue]
```

## Specialist Principles Applied

**Connector:** Patterns across clients only — never surface client-specific confidential details in cross-client context. Synthesis operates at portfolio level. Outputs are always seller-only.

**Coach:** Trend detection requires 3+ data points. Score from session evidence. Decay signals flagged with root cause hypothesis, not just observation.

## Output Labeling

`SELLER-ONLY — NOT FOR CLIENT SHARING`. This output contains stakeholder political intelligence, portfolio analysis, and cross-client patterns that are never appropriate for any client to see.

## Memory Write Discipline

The Weekly Review may propose updates to:
- `account.yaml.engagement_momentum` if health changes meaningfully
- `account.yaml.relationship_status` if status transition is observed
- New session log entries for the review itself (type: review)

All writes follow the confirmation gate.
