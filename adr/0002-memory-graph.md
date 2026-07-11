# ADR 0002 — The Memory Graph as Core Product

**Status:** Accepted
**Date:** 2026-07-11
**Deciders:** Founder
**Traces To:** PRODUCT_CONSTITUTION.md §Principle 1, §Principle 7; Strategic Foundation Document §9, §10; PRD §16 (Core Domain Objects), FR-15 (Decision Graph Construction); DECISION_FREEZE.md §Product Philosophy

---

## Context

When designing the core architecture of BoardMemory, the team needed to decide what constitutes the *product itself* — the thing that creates and retains value for the customer over time.

Several candidates were considered:

1. **Document storage** — the product is the repository of uploaded files (agendas, minutes, legal opinions)
2. **AI assistant** — the product is the conversational AI that answers questions about past decisions
3. **Workflow engine** — the product is the process automation that guides users through board meetings
4. **Board portal** — the product is the collaborative workspace for board members
5. **Decision Graph** — the product is the linked network of decisions, reasoning, people, evidence, and relationships

Options 1–4 are common patterns in enterprise software. Each captures some value but loses the core differentiator: **connected reasoning that compounds over time**.

Documents alone are files without context. AI alone is an interface without authoritative data. Workflow alone is process without memory. A portal alone is collaboration without persistence of judgment.

## Decision

**The Memory Graph (Decision Graph) is the product.**

The Decision Graph is the linked network of Decision, Meeting, Resolution, Person, Organization, Regulation, Risk, Assumption, Obligation, Evidence, Action Item, and Relationship records. It is not a feature of the product — it *is* the product.

Specifically:

- **Decisions are first-class objects** — not metadata on documents, not chat transcripts, not workflow outputs
- **Relationships are first-class concepts** — every relationship carries business meaning and is a typed, directional edge in the graph
- **Documents are evidence** — supporting artifacts linked to decisions, not the primary data structure
- **AI is the interface** — a retrieval and explanation layer over the graph, never the system of record
- **The graph compounds** — each new decision, linked to prior decisions, increases the value of the entire network

The 12 Core Domain Objects and 14 Relationship Types defined in the Domain Model form the vocabulary of this graph. The 25 logical tables in the Schema Design persist it. The Decision Graph Construction service (FR-15) builds it. The Rationale Retrieval service (FR-16) reads it.

## Consequences

### Positive

- **Compounding value** — unlike document stores, the graph becomes more valuable with every linked decision
- **Structural moat** — competitors cannot replicate the graph without the same disciplined capture process
- **AI grounding** — AI responses are always attributable to specific graph nodes, preventing hallucination from becoming institutional memory
- **Expansion-ready** — the graph is typed but not board-specific; future workflows (compliance, contracts, trade) plug into the same graph without re-architecture
- **Audit-ready** — every node carries creator, timestamp, approval history, and relationship edges

### Negative

- **Higher capture friction** — users must provide structured reasoning, not just upload files
- **Graph integrity burden** — every feature must preserve relationship integrity and bidirectional traceability
- **Slower initial value** — the graph needs several complete Meeting → Decision Graph cycles before its compounding value is visible

### Neutral

- FR-15 specifies the graph as a generic graph over typed objects (not a board-specific data structure), even though V1 populates it with board data only — this is deliberate architectural preparation for V2+
