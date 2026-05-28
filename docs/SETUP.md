# Setup Guide — Tech Seller OS Bob Edition v2

---

## Step 1 — Install IBM Bob

1. Sign up at **bob.ibm.com/trial** (30-day trial, no credit card required)
2. Install the Bob VS Code extension
3. Authenticate the extension with your IBM Bob account

---

## Step 2 — Clone and Open the Project

```bash
git clone https://github.com/[your-username]/tech-seller-os-bob-v2
cd tech-seller-os-bob-v2
code .
```

Bob VS Code opens with the Bob panel in the sidebar.

---

## Step 3 — Switch to Advanced Mode

Open the Bob chat panel. At the bottom of the panel, click the mode selector and choose **🛠️ Advanced**.

**This is required.** Bob skills only work in Advanced mode. The other modes (Code, Ask, Plan, Orchestrator) do not load custom skills.

---

## Step 4 — Verify Skills Loaded

In the Bob chat, type:

```
What skills are available?
```

Bob should list ten Tech Seller OS skills. If it does not:
- Confirm you are in Advanced mode
- Reload the Bob VS Code window (⌘+Shift+P → "Reload Window")
- Verify `.bob/skills/` exists at the project root with ten subfolders

---

## Step 5 — Enable Skill Auto-Approve (Recommended)

Open Bob Settings → Auto-Approve → toggle **Skills** on.

Without auto-approve, Bob asks permission every time a skill activates. For Tech Seller OS where skills fire frequently, this becomes friction.

---

## Step 6 — Complete Your Seller Identity

Open `memory/seller/IDENTITY.md` and fill it in completely. Take 15-20 minutes. This file is the foundation — every skill reads it on activation. Hint: use Bob to help you write it.

Test it:
```
Confirm you understand my identity by summarizing who I am and how I operate.
```

---

## Step 7 — Configure Your Portfolio

Open `memory/seller/profile.yaml` and fill in:
- Your solution domains and products
- Your maturity dimensions (or use defaults)
- Your coaching dimensions (or use defaults)
Hint: use Bob to help you with this

Test it:
```
Summarize my portfolio and the objection patterns I face.
```

---

## Step 8 — Add Your First Client

Copy the template:

```bash
cp -r memory/clients/_template memory/clients/[your-client-slug]
```

Then fill in `account.yaml` (at minimum). For Tier 1 clients, that's all you need.



Test a skill:

```
Prep me for an upcoming meeting with [client name]
```

The `pre-meeting-cockpit` skill should auto-activate.

---

## Step 9 — Explore the First Heartland Example

The repository includes a fully populated example client at `docs/examples/clients/first-heartland-bank/`. Use it to understand what a populated engagement looks like before building your own.

Try:
```
What do I know about First Heartland Bank?
```

Bob reads the example files and produces a synthesis.

You can ask Bob to populate the client memory template files with the example data so you can test all functionality.

---

## Working with Skills

### How skills activate

Bob automatically determines when to activate a skill based on your natural language. Examples:

| You say... | Skill that activates |
|------------|----------------------|
| "Prep for my Acme meeting tomorrow" | `pre-meeting-cockpit` |
| "I just got off a call with Acme — here are my notes" | `post-meeting-debrief` |
| "Ingest this annual report" | `signal-ingestion` |
| "What's my territory health this week?" | `weekly-review` |
| "Assess Acme's current state" | `technical-assessment` |
| "Generate use cases for Acme" | `use-case-generation` |
| "Diagram Acme's current architecture" | `architecture-diagrams` |
| "Build a POV for the Acme CFO" | `pov-construction` |
| "Map the Acme stakeholders" | `stakeholder-map` |
| "Sequence the Acme roadmap" | `roadmap-sequencing` |

### Triggering Devil's Advocate

Devil's Advocate does not auto-activate. Trigger it explicitly:

```
Run Devil's Advocate on the POV you just produced.
```

Or inline for high-stakes deliverables:

```
Build a POV for the Acme CFO and run Devil's Advocate before finalizing.
```

### Memory writes

Skills never auto-write to memory. They surface proposed updates in a structured review format:

```
PROPOSED MEMORY UPDATE
File: memory/clients/acme/client.yaml
Section: signals.technical
Entry: [content]

Confirm to add / Modify before adding / Reject
```

You decide what gets written.

---

## Troubleshooting

**Skills not appearing**
- Confirm Advanced mode is active
- Reload VS Code window
- Check `.bob/skills/` contains ten subfolders each with a `SKILL.md`

**Skill activates but produces wrong output type**
- Check the YAML front matter in the relevant `SKILL.md` — the `description` field controls activation
- Strengthen the description to better match your typical phrasing

**Bob asks for files you've already provided**
- Bob folder mentions are non-recursive
- Always reference specific files with `@/path/to/file.yaml`

**Portfolio data leaking into client-facing outputs**
- This is enforced by `.bob/rules/03-portfolio-firewall.md`
- If you see a violation, report the specific output to improve the rules
- Apply the seller's judgment as the final filter

---

## Bobcoin Usage Guide

Approximate cost per workflow:

| Workflow | Approximate Cost |
|----------|-----------------|
| Pre-meeting cockpit (full prep) | 2-4 coins |
| Post-meeting debrief | 1-2 coins |
| Signal ingestion (1 document) | 0.5-1 coin |
| Weekly review | 3-5 coins |
| Technical assessment | 2-3 coins |
| Use case generation | 1-2 coins |
| POV construction | 1-2 coins |
| Devil's Advocate review | 1-2 coins |

Your 40-coin trial covers initial setup plus several complete engagement workflows.
