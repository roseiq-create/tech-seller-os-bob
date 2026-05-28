# Tech Seller OS — IBM Bob Edition v2
## Enforced Architecture Configuration

---

## SYSTEM IDENTITY

Tech Seller OS is an agentic operating system for enterprise technical sellers — solutions engineers, presales architects, technical sales executives, and technology strategists. It is **not** for account executives. The audience distinction is enforced throughout the system.

This is the v2 skills-driven architecture for IBM Bob. Workflows are implemented as native Bob skills in `.bob/skills/` with auto-activation, supporting file references, and explicit tool boundaries. The previous v1 single-mode architecture has been replaced.

---

## OPERATING MODE — ENFORCED

**Required mode: Advanced.** Skills are only available in Bob's Advanced mode. All other modes (Code, Ask, Plan, Orchestrator) are out of scope for Tech Seller OS work.

If you are not in Advanced mode, switch before continuing. Do not attempt Tech Seller OS workflows in other modes — the skills will not load.

---

## CORE PRINCIPLES — HARD RULES

These principles are non-negotiable. They are enforced by `.bob/rules/` files and by every skill's instructions.

1. **Suggestion-first ingestion.** No write to memory without explicit confirmation from the seller.
2. **Portfolio firewall.** No portfolio data — vendor names, commercial context, pricing, internal positioning — in any client-facing output.
3. **Attribution discipline.** Every numerical claim, every factual claim about a client or industry, must be traceable to a source file. Unsourced claims are labeled "Source needed."
4. **Seller-only artifacts are absolute.** Stakeholder maps, coach scores, connector patterns, portfolio alignment — never surface in client-facing materials under any circumstances.
5. **Identity before action.** `memory/seller/IDENTITY.md` is read at the start of every skill execution. No exceptions.
6. **The seller's judgment is the final filter.** The system surfaces. The seller decides.

---

## FILE SYSTEM ARCHITECTURE

```
tech-seller-os-bob/
├── AGENTS.md                          ← This file. Enforced architecture config.
├── .bob/
│   ├── skills/                        ← Native Bob skills — auto-activate on request
│   │   ├── pre-meeting-cockpit/
│   │   ├── post-meeting-debrief/
│   │   ├── signal-ingestion/
│   │   ├── weekly-review/
│   │   ├── technical-assessment/
│   │   ├── use-case-generation/
│   │   ├── architecture-diagrams/
│   │   ├── pov-construction/
│   │   ├── stakeholder-map/
│   │   └── roadmap-sequencing/
│   └── rules/                         ← Global enforcement — applies to every skill
│       ├── 00-core-principles.md
│       ├── 01-memory-protocol.md
│       ├── 02-output-standards.md
│       └── 03-portfolio-firewall.md
├── memory/
│   ├── seller/
│   │   ├── IDENTITY.md                ← Loaded by every skill
│   │   ├── profile.yaml               ← Loaded by skills that need portfolio context
│   │   ├── context-strategy.md
│   │   └── pov-corpus.yaml
│   ├── clients/[slug]/
│   │   ├── account.yaml               ← Loaded by every client-scoped skill
│   │   ├── ENGAGEMENT.md
│   │   ├── client.yaml
│   │   ├── sessions.yaml
│   │   └── stakeholder-map.yaml      ← SELLER-ONLY — restricted access
│   ├── industries/[slug]/
│   └── portfolio-alignment/[slug].yaml  ← SELLER-ONLY — restricted access
├── stack/                             ← Reference documentation
├── artifacts/                         ← Generated deliverables
└── docs/examples/                     ← First Heartland Bank populated example
```

---

## SKILL ROUTING — AUTO-ACTIVATION TRIGGERS

Bob auto-activates skills based on natural language triggers. The skill descriptions in each `SKILL.md` define the activation conditions. The mapping below is the authoritative routing table.

| Skill | Activation Triggers |
|-------|---------------------|
| `pre-meeting-cockpit` | "prep for [client] meeting", "meeting brief", "upcoming meeting prep" |
| `post-meeting-debrief` | "debrief", "capture session", "log meeting", "session notes" |
| `signal-ingestion` | "ingest", "extract signals", "analyze document", "research [company]" |
| `weekly-review` | "weekly review", "territory review", "cross-client review" |
| `technical-assessment` | "assess [client] current state", "landscape assessment", "maturity assessment" |
| `use-case-generation` | "generate use cases", "use case library", "identify opportunities" |
| `architecture-diagrams` | "diagram [client]", "current state diagram", "target state diagram" |
| `pov-construction` | "build POV", "construct POV", "reframe for [audience]" |
| `stakeholder-map` | "map stakeholders", "stakeholder analysis", "political map" |
| `roadmap-sequencing` | "sequence roadmap", "roadmap [client]", "horizon plan" |

---

## SKILL EXECUTION CONTRACT

Every skill follows the same execution contract:

1. **Identity load.** Read `memory/seller/IDENTITY.md` before any analysis.
2. **Portfolio load (if relevant).** Read `memory/seller/profile.yaml` for skills that bridge to portfolio.
3. **Client context load.** Read `memory/clients/[slug]/account.yaml` first to determine engagement tier, then load tier-appropriate files.
4. **Skill-specific instructions.** Each `SKILL.md` defines the workflow.
5. **Output classification.** Every output is labeled "SELLER-ONLY — INTERNAL" or "CLIENT-FACING" at the top.
6. **Memory write protocol.** No writes without explicit confirmation. Surface proposed writes in a structured format.
7. **Session log proposal.** Significant workflows propose session log entries for `sessions.yaml`.

---

## THREE-TIER CLIENT ENGAGEMENT MODEL

Determined by `engagement_tier` field in `account.yaml`. Controls which files skills attempt to load.

- **Tier 1 (Signal Capture):** `account.yaml`, `sessions.yaml`
- **Tier 2 (Active Technical Engagement):** All Tier 1 files plus `ENGAGEMENT.md`, `client.yaml`, `stakeholder-map.yaml`
- **Tier 3 (Strategic Partnership):** All Tier 2 files plus `memory/industries/[slug]/`, `memory/portfolio-alignment/[slug].yaml`

---

## RESTRICTED ACCESS FILES — ENFORCED

These files are seller-only and **never** appear in client-facing outputs. Skills that touch these files must label outputs accordingly and apply the portfolio firewall on any derivative work.

- `memory/seller/profile.yaml` — your portfolio
- `memory/portfolio-alignment/*.yaml` — per-client portfolio fit
- `memory/clients/*/stakeholder-map.yaml` — political intelligence
- Any output from `stakeholder-map` or `weekly-review` skills
- Any coach scoring or cross-client synthesis

---

## NINE SPECIALIST AGENT PERSONAS — REFERENCE

The previous v1 architecture exposed nine specialist agents as separate Bob modes. In v2, these personas are **embedded within skills** rather than being separately invokable. Each skill applies the principles of one or more specialists internally.

| Specialist | Embedded In Skills |
|-----------|--------------------|
| The Researcher | `signal-ingestion`, `pre-meeting-cockpit` |
| The Architect | `technical-assessment`, `use-case-generation`, `roadmap-sequencing` |
| The Strategist | `pov-construction`, `pre-meeting-cockpit`, `architecture-diagrams` |
| The Scribe | `post-meeting-debrief`, all skills (output discipline) |
| The Devil's Advocate | Triggered explicitly via "challenge [artifact]" — runs as adversarial pass on any skill output |
| The Coach | `post-meeting-debrief`, `weekly-review` |
| The Connector | `weekly-review` |
| Architecture Diagrams | `architecture-diagrams` |
| Stakeholder Map | `stakeholder-map`, `pre-meeting-cockpit` (read-only) |

Full specialist persona definitions are preserved in `stack/layer-3-skills/specialist-personas.md` for reference.

---

## DEVIL'S ADVOCATE — CROSS-SKILL ENHANCEMENT

The Devil's Advocate runs as an explicit adversarial pass on any skill output. Trigger by asking:

```
Run Devil's Advocate on the [skill name] output.
```

Or for high-stakes deliverables, request inline:

```
Build [POV / assessment / roadmap] for [client] and run Devil's Advocate before finalizing.
```

The Devil's Advocate is intentionally **not** auto-fired on every skill — it would add noise to lower-stakes workflows. The seller decides when adversarial review is warranted.

---

## FIRST RUN — SETUP CHECKLIST

1. Open this folder in VS Code with IBM Bob installed.
2. Switch to **Advanced mode** in Bob.
3. Verify skills are loaded: open a chat and type `What skills are available?` — Bob should list the ten Tech Seller OS skills.
4. Complete `memory/seller/IDENTITY.md` — this is the foundation of every skill.
5. Complete `memory/seller/profile.yaml` — required for portfolio-bridging skills.
6. Add your first client by copying `memory/clients/_template/` to `memory/clients/[your-client-slug]/` and filling in the files.
7. Test by running a Pre-Meeting Cockpit skill against your client.

---

## VERSION

Tech Seller OS Bob Edition v2.0 — May 2026
Architecture: Skills-driven with enforced boundaries
Previous architecture (v1 — custom modes): deprecated, see `docs/v1-archive/` if needed
Contact: info@roseiq.co
License: CC BY-NC-SA 4.0
