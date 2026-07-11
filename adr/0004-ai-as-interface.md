# ADR 0004 — AI as Interface, Not System of Record

**Status:** Accepted
**Date:** 2026-07-11
**Deciders:** Founder
**Traces To:** PRODUCT_CONSTITUTION.md §Principle 6; Strategic Foundation Document §10, §13; DECISION_FREEZE.md §Product Philosophy; System Architecture §7 (AI Retrieval Layer), AP5; PRD FR-18, §19 (Product Constraints); IMPLEMENTATION_RULES.md §Rule 6

---

## Context

BoardMemory captures and preserves organizational reasoning. AI is an integral part of the product vision — the Strategic Foundation explicitly states "AI is the interface; the memory graph is the product."

However, the role of AI needed to be precisely bounded to prevent a common architectural failure: allowing an AI system to become the de facto system of record, where users trust AI-generated responses as authoritative facts rather than as retrieval from a governed data store.

Three architectural positions were evaluated:

### Position A — AI as Core Intelligence

- AI generates insights, identifies patterns, and proactively surfaces connections between decisions
- AI responses are stored as first-class objects in the Decision Graph
- The system becomes an "AI governance advisor"
- **Risk:** AI-generated content becomes indistinguishable from human-captured reasoning. Hallucinated knowledge could become institutional memory.

### Position B — AI as Co-Author

- AI assists in drafting rationale, suggesting alternatives, and pre-filling assumption fields
- AI-generated content is editable and eventually approved by humans
- **Risk:** Blurs the line between captured reasoning and generated reasoning. Over time, organizations may not know which "reasoning" was actually reasoned by humans vs. suggested by AI.

### Position C — AI as Read-Only Interface

- AI provides natural-language access to already-captured rationale via the Decision Graph
- AI retrieves, summarizes, and explains — but never writes to the graph
- AI responses are always attributable to specific graph nodes
- The Decision Graph remains the sole system of record
- **Risk:** Limited AI utility in V1; users cannot leverage AI during the capture phase.

## Decision

**AI is the interface to the Decision Graph. It is never the system of record.**

Specifically:

### AI May

- **Retrieve** — search the Decision Graph and return matching decisions, rationale, evidence, and relationships
- **Summarize** — condense retrieved rationale into natural-language explanations
- **Explain** — answer questions like "why was this decision made?" by composing answers from graph data
- **Suggest** — surface potentially relevant past decisions during new decision capture (future, not V1)

### AI May Never

- **Invent** — generate organizational history that does not exist in the Decision Graph
- **Modify** — alter approved records, relationships, or rationale
- **Replace** — serve as the authoritative source of truth for any business fact
- **Store** — persist AI-generated content as canonical Decision Graph data

### Architectural Enforcement

The System Architecture enforces this through **AP5 (AI Retrieval Is Read-Only)**:

- The AI Retrieval Layer sits *over* the Search Service and Rationale Retrieval Service
- It has **no path** back into any write-capable Core Service (Meeting Management, Decision Capture, Decision Graph, Document Generation)
- Every AI response must derive from data already stored in the canonical model
- Generated responses must be **attributable** — traceable to specific graph nodes

The Product Constraints (PRD §19) further state: "The Decision Graph, not any document store or AI chat surface, must remain the system of record — no feature may reduce it to a side effect of a conversational interface."

## Consequences

### Positive

- **Trust and auditability** — every AI response can be verified against the graph; no "black box" answers
- **Hallucination prevention** — AI cannot create false institutional memory because it cannot write to the graph
- **Governance integrity** — the Decision Graph remains the single source of truth, per AP1
- **Regulatory defensibility** — auditors can inspect the graph directly; they never need to trust AI output
- **Clean expansion path** — AI capabilities can be expanded (e.g., pattern detection, proactive surfacing) without architectural change, as long as the read-only boundary is preserved

### Negative

- **Limited V1 AI scope** — AI in V1 is primarily retrieval (FR-18), not intelligent assistance during capture
- **User expectation management** — users familiar with ChatGPT-style AI may expect the system to "know" things it hasn't been told; AI can only retrieve what was captured
- **No AI-assisted drafting in V1** — rationale, alternatives, and assumptions must be manually entered

### Neutral

- Position B (AI as Co-Author) is not permanently rejected — it is deferred to future consideration, contingent on governance approval and clear attribution mechanisms that distinguish AI-suggested content from human-captured reasoning
- The read-only architectural boundary (AP5) makes it safe to experiment with AI capabilities in future versions without risking data integrity
