# Tech Seller OS — Portfolio Firewall
# Hard enforcement: commercial and portfolio data never reaches client-facing outputs

## The Firewall Rule

Portfolio data never appears in client-facing outputs. This includes:

- Solution names from `memory/seller/profile.yaml`
- Vendor relationships and partnerships
- Pricing, commercial context, internal product positioning
- Portfolio fit scores and analysis from `memory/portfolio-alignment/`
- Internal product roadmap references

This rule has no exceptions. It applies regardless of how relevant the portfolio data seems to the client's situation.

## What Is Behind the Firewall

- `memory/seller/profile.yaml` — full solution portfolio
- `memory/portfolio-alignment/[slug].yaml` — portfolio fit per client
- Any output from `weekly-review` skill (Connector + Coach principles)
- Any output from `stakeholder-map` skill (political intelligence)
- Internal engagement notes marked seller-only
- Coach scores in any session log

## What Is Visible to Clients

- Client's own stated priorities and challenges
- Technology landscape data the client has contributed or confirmed
- Use cases and roadmap elements the seller has shared with the client
- Architecture diagrams built from client-documented landscape (using generic capability labels for any portfolio-side suggestions)
- Meeting briefs and follow-up artifacts explicitly produced as client-facing

## Portfolio Bridging — Two-Version Discipline

When a skill produces portfolio bridging analysis (connecting client context to seller's solutions), it must produce two versions clearly labeled:

**1. INTERNAL VERSION (seller-only):**
- Full portfolio context, fit scores, competitive angles
- Specific vendor recommendations
- Pricing and commercial considerations
- Entry-point conversation framing

**2. CLIENT-FACING VERSION:**
- Reframed as client capability response
- Generic capability labels — no vendor product names
- Outcomes language — no commercial language
- Specific to the client's stated problem

Never merge the two. If a document contains any portfolio data, the entire document is internal-only.

## Diagram Firewall

Architecture diagrams produced for client sharing only show:
- Components the client has explicitly documented in `memory/clients/[slug]/client.yaml` landscape
- Target state components based on client-stated goals
- Industry-standard reference architectures with generic labels

Portfolio vendor product names from `profile.yaml` do not appear as node labels in client-facing diagrams. Use the substitution table in `02-output-standards.md`.

## Audit Discipline

Every skill that touches portfolio data is responsible for:

1. Checking output classification (Internal vs. Client-Facing)
2. Applying substitutions for client-facing outputs
3. Producing an explicit substitution table when both versions are generated
4. Labeling all outputs at the top with the audience classification

The seller's judgment is the final audit. If you see portfolio data leaking into client-facing outputs, stop and correct before sharing.
