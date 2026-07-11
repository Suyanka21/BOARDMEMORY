# BoardMemory

**Enterprise Decision Memory for Board Governance**

> *Documents are evidence. Decisions are knowledge. Reasoning is an organizational asset. AI is the interface. The Memory Graph is the product.*

---

## What Is BoardMemory?

BoardMemory is an AI-powered governance platform that transforms board decisions into a living organizational reasoning system. Instead of merely storing meeting minutes and resolutions, it captures the assumptions, alternatives considered, legal advice, risks, evidence, approvals, and strategic intent behind every important decision — linking them into a searchable **Decision Graph** that becomes the organization's institutional memory.

Unlike traditional board portals that preserve documents, **BoardMemory preserves judgment**.

It enables boards, executives, legal teams, compliance officers, auditors, and future AI systems to understand not only *what* decisions were made, but *why* they were made, what assumptions supported them, how they relate to subsequent decisions, and when those assumptions are no longer valid.

---

## The Problem

Organizations remember documents. They rarely remember *why* decisions were made.

As people leave the organization, institutional reasoning disappears. Enterprise systems preserve files — but not the knowledge, assumptions, rationale, approvals, and context that produced those files.

BoardMemory solves this by capturing, preserving, and retrieving organizational reasoning.

---

## Category

**Enterprise Decision Memory** — software that preserves organizational reasoning, assumptions, approvals, and institutional knowledge so that decisions become reusable rather than repeatedly recreated.

BoardMemory defines and builds this category. It is not:

- Document Management Software
- Governance Portal
- LegalTech / RegTech
- Enterprise Search or Knowledge Base
- Generic AI Assistant or Chatbot

---

## Target Customer

Mid-sized regulation-intensive organizations (50–500 employees) that depend on board governance and institutional accountability.

**Segments:** Holding companies · Investment firms · Family businesses · Professional service firms · NGOs · Large SACCOs · Regional companies

**Geography:** Kenya and East Africa (initial focus), with eventual expansion across the African continent.

**Personas:**

| Persona | Pain Point |
|---------|-----------|
| Corporate Secretary | "We spend three days reconstructing board history." |
| External Legal Counsel | "We repeat the same legal analysis." |
| Board Director / CEO | "The people who made this decision left." |
| Auditor | "Show us why this decision was approved." |
| Family Office Principal | "No one remembers why this trust was structured this way." |

---

## Core Workflow (V1)

BoardMemory V1 delivers one exceptional workflow — not an enterprise platform:

```
Create Board Meeting
    → Upload agenda & supporting documents
        → Record discussion
            → Capture reasoning, assumptions, alternatives
                → Vote
                    → Approve
                        → Generate minutes
                            → Generate resolution
                                → Generate action register
                                    → Build Decision Graph
                                        → Store permanently
```

---

## Architecture Overview

BoardMemory follows a layered, governance-driven architecture:

```
Client Layer
    │
    ▼
Application Layer
    │
    ▼
Domain Layer (9 Aggregates, 6 Value Objects, 6 Domain Services)
    │
    ▼
Persistence Layer (25 Logical Tables)
    │
    ├── AI Retrieval Layer (read-only)
    └── Document Generation Layer (compose-only)
```

### Core Domain Objects

| Object | Purpose |
|--------|---------|
| Decision | The central knowledge unit — an approved/rejected choice with its rationale |
| Meeting | A single board meeting instance |
| Resolution | Formal document generated from an approved Decision |
| Person | Individual participant — director, secretary, counsel, auditor |
| Organization | The customer entity whose governance is recorded |
| Regulation | Regulatory reference relevant to a Decision |
| Risk | Risk acknowledged or accepted as part of a Decision |
| Assumption | Financial, legal, or operational assumption underlying a Decision |
| Obligation | Compliance or contractual obligation connected to a Decision |
| Evidence | Supporting document attached to a Decision or Meeting |
| Action Item | Follow-up task generated from a Decision |
| Relationship | Explicit, typed link connecting any two domain objects |

---

## Repository Structure

```
BOARDMEMORY/
│
├── README.md                          ← You are here
├── AGENTS.md                          ← AI operating instructions
├── LICENSE
├── .gitignore
│
├── docs/                              ← Architectural & governance documents
│   ├── Strategic_Foundation_Document_v1.0.docx
│   ├── Founder_Narrative_and_Venture_Journey.docx
│   ├── BoardMemory_PRD_v1.0.pdf
│   ├── Domain_Model_Board_Governance_V1.pdf
│   ├── Schema_Design.pdf
│   ├── System_Architecture_Phase_1.4.pdf
│   ├── BoardMemory_API_Contract_Specification.pdf
│   ├── DECISION_FREEZE.md
│   ├── PRODUCT_CONSTITUTION.md
│   ├── ARCHITECTURE_INDEX.md
│   ├── IMPLEMENTATION_RULES.md
│   ├── IMPLEMENTATION_ROADMAP.md
│   └── CHANGELOG.md
│
├── adr/                               ← Architecture Decision Records
│   ├── 0001-category-thesis.md
│   ├── 0002-memory-graph.md
│   ├── 0003-relational-canonical-model.md
│   └── 0004-ai-as-interface.md
│
├── frontend/                          ← Frontend implementation (Milestone 2+)
├── backend/                           ← Backend implementation (Milestone 3+)
├── infrastructure/                    ← Infrastructure configuration
├── scripts/                           ← Development & operational scripts
│
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md
│   │   ├── feature_request.md
│   │   └── architectural_issue.md
│   ├── PULL_REQUEST_TEMPLATE.md
│   └── workflows/
│
└── .vscode/
    ├── extensions.json
    └── settings.json
```

---

## Recommended Reading Order

Every new contributor should read the documents in this order:

1. `README.md` ← You are here
2. `docs/PRODUCT_CONSTITUTION.md`
3. `docs/DECISION_FREEZE.md`
4. `docs/Strategic_Foundation_Document_v1.0.docx`
5. `docs/Founder_Narrative_and_Venture_Journey.docx`
6. `docs/BoardMemory_PRD_v1.0.pdf`
7. `docs/Domain_Model_Board_Governance_V1.pdf`
8. `docs/Schema_Design.pdf`
9. `docs/System_Architecture_Phase_1.4.pdf`
10. `docs/BoardMemory_API_Contract_Specification.pdf`
11. `docs/IMPLEMENTATION_RULES.md`
12. `docs/IMPLEMENTATION_ROADMAP.md`
13. `AGENTS.md`

This sequence is mandatory. Skipping earlier documents increases the risk of architectural drift.

---

## Governance

BoardMemory follows strict governance principles:

- **Product Constitution** governs all product decisions
- **Decision Freeze** locks strategic decisions for V1
- **Architecture Index** maps every document and its authority
- **Implementation Rules** define how architecture becomes software
- Every proposed feature must pass the **7-question Decision Test**

In the event of conflict, precedence follows: Constitution → Decision Freeze → Strategic Foundation → PRD → Domain Model → Schema → Architecture → API Contracts → Implementation docs.

---

## North Star

> Every significant organizational decision should remain explainable years after it was made.

Success is measured by an organization's ability to answer: **"Why was this decision made?"** — without reconstructing history.

---

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

## Contributing

All contributions must comply with the Product Constitution, respect the Decision Freeze, and follow the Implementation Rules. See `AGENTS.md` for AI-specific operating instructions.

Every Pull Request must:

- Reference an approved implementation task
- Reference affected architectural artifacts
- Preserve traceability
- Include tests where appropriate
- Pass governance review

---

*BoardMemory — Preserving institutional reasoning, one decision at a time.*
