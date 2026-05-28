# Tech Seller OS — Memory Protocol
# Enforced rules for reading and writing memory files

## Session Start Protocol — Enforced

Every skill execution loads files in this order:

1. `memory/seller/IDENTITY.md` — always
2. `memory/seller/profile.yaml` — for skills involving portfolio or maturity scoring
3. `memory/clients/[slug]/account.yaml` — first read for any client-scoped skill, to determine tier
4. Additional client files based on tier (see Tier Mapping below)
5. Industry context files if Tier 3 client

Files are referenced explicitly in each skill's `SKILL.md`. Bob loads them automatically when the skill activates.

## Tier Mapping

Read `account.yaml.engagement_tier` to determine which additional files to load:

**Tier 1 (Signal Capture):**
- `account.yaml`, `sessions.yaml`

**Tier 2 (Active Technical Engagement):**
- All Tier 1 files
- `ENGAGEMENT.md`
- `client.yaml`
- `stakeholder-map.yaml` (seller-only — only loaded by stakeholder-related skills)

**Tier 3 (Strategic Partnership):**
- All Tier 2 files
- `memory/industries/[slug]/*` if industry context exists
- `memory/portfolio-alignment/[slug].yaml` (seller-only)

## Write Protocol — Confirmation Gate

Memory writes follow a strict gate. Every proposed write is formatted as:

```
PROPOSED MEMORY UPDATE
File: memory/clients/[slug]/client.yaml
Section: signals.business
Entry:
  - text: "[signal text]"
    source: "[specific source]"
    category: Business
    date: 2026-05-27
    importance: High
    relevance: "[why this matters for the engagement]"
    voice: researcher

Confirm to add / Modify before adding / Reject
```

The seller's explicit confirmation is required. Skills may batch multiple proposed writes in a single review, but each must be confirmable individually.

## File Hierarchy of Precedence

When information conflicts across files, precedence is:

1. `IDENTITY.md` (seller's operating principles override everything)
2. Client-specific files (override industry defaults)
3. Industry context files
4. Portfolio profile defaults

Skills must respect this hierarchy when reasoning across files.

## Session Logging Discipline

After meaningful client-scoped workflows, skills propose a session log entry for `memory/clients/[slug]/sessions.yaml`. The proposal includes:

- Date, type (internal-prep / client-meeting / call / review / workshop / ebr)
- Attendees (for client meetings)
- Key outputs produced
- Decisions made
- Open questions created
- Coach score if applicable

Auto-write is prohibited. The seller confirms or modifies.
