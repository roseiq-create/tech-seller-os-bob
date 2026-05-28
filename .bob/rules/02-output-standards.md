# Tech Seller OS — Output Standards
# Quality and format requirements for all skill outputs

## The Two Output Audiences

Every output serves one of two audiences:

**Seller-facing outputs (internal):** Include portfolio context, coach scores, stakeholder political intelligence, cross-client patterns, raw analysis. Preparation tools. Labeled `SELLER-ONLY — INTERNAL`.

**Client-facing outputs:** Strip portfolio data, internal scores, political intelligence. Professional artifacts ready for client sharing. Labeled `CLIENT-FACING`. Portfolio firewall applied (see rule 03).

Always label which type at the top of the output.

## Attribution Discipline for Numerical Claims

Any numerical claim — costs, durations, headcount, percentages, ROI, market sizing, revenue impact, peer benchmarks — must be traceable to a source file or external citation. Numbers without a source are labeled:

- `Estimate — source needed` for rough projections requiring validation
- `Industry rule-of-thumb` for general patterns applied to this client
- `Order of magnitude only` for ballpark figures used to frame conversations

Never present invented numbers with the same authority as sourced numbers. A CFO reading the output should distinguish at a glance between:

1. A sourced fact ("162 point-to-point integrations — source: client.yaml")
2. An estimate requiring validation ("Estimate — source needed: $10-12M for integration build")
3. An industry pattern applied ("Industry rule-of-thumb: 18-24 months for integration architecture programs at this scale")

If no cost source data exists in memory, do not produce a fabricated business case. Produce a business case structure with explicit "Source needed" labels for the seller to populate.

## Diagram Firewall Specifics

Vendor product names from `memory/seller/profile.yaml` never appear as node labels in client-facing diagrams. Use generic capability labels that preserve architectural specificity:

| Portfolio Vendor | Client-Facing Label |
|------------------|--------------------|
| watsonx.data | Cloud Data Lakehouse (preserve "Apache Iceberg" if relevant) |
| Confluent | Real-Time Streaming Platform |
| watsonx.ai | ML Platform (preserve "Multi-Model Support" if relevant) |
| watsonx.governance | AI Governance Framework or Unified Data Governance |
| watsonx.orchestrate | Agentic Automation Platform |

The client's own vendor relationships — documented in `memory/clients/[slug]/client.yaml` landscape sections — are NOT subject to this firewall. Temenos T24, Teradata, MicroStrategy, FICO, and similar named vendors in the client's documented landscape appear in client-facing diagrams unchanged.

Diagram outputs must state "Internal Version" or "Client-Facing Version" at the top.

## Format Standards

**Artifacts (POVs, Briefs, Strategy Documents):**
- Open with a crisp summary stating the conclusion
- Headers for navigation, not decoration
- Bullets for lists of three or more parallel items
- Tables for comparisons and scoring
- Close with clear next steps — who does what by when

**Analysis outputs (Assessments, Maturity Scores, Gap Analysis):**
- Lead with the finding, not the methodology
- Score + rationale, not rationale + score
- Evidence cited for every score
- Gaps called out explicitly — do not omit weak areas

**Conversational outputs (Meeting Prep, Coaching, Research Summaries):**
- Professional but direct register
- Short paragraphs or bullets — not walls of text
- Flag urgency when time-sensitive items surface

## Length Calibration

- POVs: 400–700 words client-facing, 600–900 with delivery notes (seller-facing)
- Meeting briefs: One page, scannable in two minutes
- Architecture assessments: As long as evidence warrants — no filler
- Session summaries: 200–400 words
- Signal extractions: Structured items, not prose

## What Not To Do

- Never produce generic industry observations as client-specific insights
- Never pad outputs with qualifications and caveats that undermine the point
- Never include both "however" and "that said" in the same paragraph
- Never close an output with "Let me know if you need anything else"
- Never produce a deliverable without a clear next step or action
- Never present invented numbers with the same authority as sourced numbers
- Never include seller portfolio vendor names as node labels in client-facing diagrams
- Never auto-write to memory without explicit seller confirmation
