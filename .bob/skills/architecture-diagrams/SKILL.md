---
name: architecture-diagrams
description: Generate current state, target state, and gap visualization architecture diagrams from client landscape data. Produces Mermaid (for collaborative tools) and optionally HTML (for client-facing exports). Applies portfolio firewall — always generates both Internal Version (vendor names) and Client-Facing Version (generic capability labels) when portfolio context is relevant. Use when the seller asks to diagram an architecture, generate a current or target state diagram, or visualize a domain.
---

# Architecture Diagrams

You are running the Architecture Diagrams skill. This skill produces visual artifacts from client landscape data. Strict portfolio firewall enforcement.

## Files to Load

1. `memory/seller/IDENTITY.md`
2. `memory/seller/profile.yaml` — to know which vendor names require firewall substitution
3. `memory/clients/[slug]/client.yaml` — landscape data is the diagram source of truth

## Diagram Types

Determine which diagram type the seller wants:

- **Current State** — what exists today, from `client.yaml.landscape.[domain].current_state`
- **Target State** — what is planned, from `client.yaml.landscape.[domain].target_state`
- **Gap Visualization** — current and target overlaid showing deltas
- **Domain Drill-Down** — single domain in detail

If not specified, default to Current State.

## Domain Scope

Diagrams can be scoped to:
- All domains (full architecture)
- Single domain (e.g., "Data & AI domain")
- Specific subset the seller requests

If not specified, ask.

## Output Format

### Mermaid (default)

```mermaid
graph TB
    %% [Client Name] — [Current State | Target State] — [Date]

    subgraph "Domain Name"
        NODE1[Component Name]
        NODE2[Component Name]
    end

    %% Connections
    NODE1 --> NODE2

    %% Styling
    style NODE1 fill:[color]
```

Color coding convention:
- Red (#ff6b6b) — critical constraints
- Yellow (#ffd93d) — warning / partial
- Green (#6bcf7f) — working or target state
- Teal (#38ada9) — strategic outcomes / business value

### HTML (when requested)

Self-contained HTML with embedded CSS. Print-ready 8.5x11 layout. Same color conventions.

## Portfolio Firewall — Two-Version Protocol

If the diagram references portfolio capabilities (target state likely does), produce two versions:

**INTERNAL VERSION (seller-only):**
- Vendor product names preserved as node labels
- Example: "Cloud Data Lakehouse - watsonx.data - Apache Iceberg"

**CLIENT-FACING VERSION:**
- Vendor product names replaced with generic capability labels per the substitution table in `02-output-standards.md`
- Example: "Cloud Data Lakehouse - Open Architecture - Multi-Engine Query"
- Client's own documented vendors (Temenos, Teradata, FICO, etc.) remain unchanged — they are the client's reality, not seller portfolio

Always produce a substitution table showing what was changed.

## Quality Standards

- Never invent components not documented in `client.yaml.landscape`
- When landscape data is sparse, produce a partial diagram and flag what is missing
- Label every diagram with: client name, date, "Current State" or "Target State", "Internal Version" or "Client-Facing Version"
- Subgraphs use domain-standard names that map to maturity dimensions

## Specialist Principles Applied

**Architecture Diagrams agent:** Work from data, not invention. Apply firewall before producing client-facing version. Flag sparse data honestly.

## Output Labeling

Always label at the top:
- "INTERNAL VERSION" or "CLIENT-FACING VERSION"
- "Current State" or "Target State" or "Gap Visualization"
- Client name and date

## Output Storage

Save final diagrams to `artifacts/[client-slug]/diagrams/` with descriptive filenames:
- `current-state-2026-05-27.md` (Mermaid in markdown wrapper)
- `target-state-data-ai-domain-2026-05-27-client.md`
- `target-state-data-ai-domain-2026-05-27-internal.md`

Propose the save location for seller confirmation before writing.
