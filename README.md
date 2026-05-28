# Tech Seller OS — IBM Bob Edition v2

**An agentic operating system for enterprise technical sellers**
**Skills-driven architecture for IBM Bob**

> **v2 architecture:** Native Bob skills with auto-activation, supporting file references, and enforced operating boundaries. AGENTS.md as enforced architecture configuration, not behavioral guidance.

---

## What This System Does

Tech Seller OS augments the judgment of enterprise technical sellers — solutions engineers, presales architects, technical sales executives, technology strategists — with a structured file-based memory system and ten specialized skills that combine the principles of nine specialist agents (Researcher, Architect, Strategist, Scribe, Devil's Advocate, Coach, Connector, Architecture Diagrams, Stakeholder Map).

Bob auto-activates skills based on your natural language. You don't choose modes. You describe what you need. Skills handle the rest.

---

## v2

**v2 (current):** Ten skills in `.bob/skills/`. Each skill auto-activates on natural language triggers, references the files it needs, applies specialist principles internally, and produces structured output. Operates in Bob's **Advanced mode**.


---

## Prerequisites

- IBM Bob installed in VS Code (30-day trial at bob.ibm.com/trial)
- Bob in **Advanced mode** (required for skills)
- Auto-approve for skills enabled (recommended): Bob Settings → Auto-Approve → Skills toggle

---

## Quick Start

```bash
# 1. Clone the repository
git clone https://github.com/[your-username]/tech-seller-os-bob-v2
cd tech-seller-os-bob-v2

# 2. Open in Bob VS Code
code .

# 3. Switch Bob to Advanced mode (bottom of chat panel)

# 4. Verify skills loaded
# In the Bob chat panel:
What skills are available?
```

Bob should list the ten Tech Seller OS skills.

---

## The Ten Skills

| Skill | Auto-activates on |
|-------|-------------------|
| `pre-meeting-cockpit` | "prep for [client] meeting" |
| `post-meeting-debrief` | "debrief [client] meeting" |
| `signal-ingestion` | "ingest [document]", "extract signals" |
| `weekly-review` | "weekly review", "territory review" |
| `technical-assessment` | "assess [client] current state" |
| `use-case-generation` | "generate use cases for [client]" |
| `architecture-diagrams` | "diagram [client] architecture" |
| `pov-construction` | "build POV for [client]" |
| `stakeholder-map` | "map stakeholders for [client]" |
| `roadmap-sequencing` | "sequence roadmap for [client]" |

**Devil's Advocate** is triggered explicitly: "Run Devil's Advocate on [artifact]".

---

## File System

```
tech-seller-os-bob/
├── AGENTS.md                          ← Enforced architecture config
├── .bob/
│   ├── skills/                        ← Ten skills, each with SKILL.md
│   └── rules/                         ← Global enforcement rules
├── memory/
│   ├── seller/                        ← Your identity, portfolio, POV corpus
│   ├── clients/                       ← One folder per active client
│   ├── industries/                    ← Industry context built over time
│   └── portfolio-alignment/           ← Commercial context (SELLER-ONLY)
├── stack/                             ← Reference documentation
├── artifacts/                         ← Generated deliverables
└── docs/examples/                     ← First Heartland Bank populated example
```

---

## First Run Setup

1. Open the project in Bob VS Code
2. Switch Bob to Advanced mode
3. Complete `memory/seller/IDENTITY.md` (template provided, hint: have Bob help you build it)
4. Configure `memory/seller/profile.yaml` with your portfolio and maturity dimensions (Hint: provide Bob portfolio files, information, URLs, etc.)
5. Test by referencing the populated example: `What do I know about First Heartland Bank?`

See `docs/SETUP.md` for detailed first-run instructions.

---

## License

CC BY-NC-SA 4.0 — Free to use, adapt, and share with attribution.

---

**RoseIQ** · info@roseiq.co
