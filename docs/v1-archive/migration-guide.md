# Migrating from v1 to v2

## What v1 Was

The v1 architecture exposed nine specialist agents (Researcher, Architect, Strategist, etc.) as Bob custom modes. Workflows required manual mode switching or routing through a single Tech Seller OS custom mode with embedded routing logic.

## What v2 Is

v2 collapses the nine agents into specialist principles embedded within ten native Bob skills. Skills auto-activate based on natural language. Bob runs in Advanced mode. Operating principles live in `AGENTS.md` (enforced architecture) and `.bob/rules/` (global enforcement).

## Migration Steps

1. **Back up your v1 memory.** Your `memory/` directory transfers to v2 unchanged — same templates, same structure. Copy it.

2. **Replace `.bob/custom_modes.yaml` with v2 files.** Delete the file. Replace with:
   - `.bob/skills/` directory containing the ten skill folders
   - `.bob/rules/` directory containing the four rules files

3. **Update `AGENTS.md`.** Replace v1 AGENTS.md with v2 version. The v2 file treats AGENTS.md as enforced architecture configuration.

4. **Switch Bob to Advanced mode.** Skills only work in Advanced mode.

5. **Enable skill auto-approve.** Bob Settings → Auto-Approve → Skills toggle on.

6. **Verify skills loaded.** In Bob chat: "What skills are available?"

## What's Preserved

- All memory files (`memory/seller/`, `memory/clients/`, `memory/industries/`, `memory/portfolio-alignment/`)
- All your IDENTITY.md, profile.yaml, client records, sessions, stakeholder maps
- All POV corpus entries
- All artifacts

## What's Replaced

- `.bob/custom_modes.yaml` (no longer needed in v2)
- v1 AGENTS.md (replaced with v2 enforced architecture version)
- v1 `.bob/rules/` (replaced with hardened v2 rules)
- v1 specialist mode prompts in `prompts/` (preserved as reference in `stack/layer-3-skills/specialist-personas.md`)

## What's Different in Practice

**v1 workflow:**
```
Switch to Tech Seller OS mode → Reference files with @ mentions → Submit prompt
```

**v2 workflow:**
```
In Advanced mode → Submit natural language request → Skill auto-activates and loads its files
```

The friction reduction is meaningful for repeated workflows.

## What You Lose

- Per-specialist file access restrictions (v1 had specialist modes that could only edit certain files). v2 enforces these through rules and skill instructions, not Bob's tool boundaries.
- The ability to invoke a specialist persona as a standalone mode. If you need that, paste the persona definition from `stack/layer-3-skills/specialist-personas.md` into the chat.
