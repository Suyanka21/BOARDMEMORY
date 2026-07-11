# ADR 0003 — Relational Canonical Model with Graph Semantics

**Status:** Accepted
**Date:** 2026-07-11
**Deciders:** Founder, Venture Foundry OS
**Traces To:** Schema Design §1–§5; System Architecture AP1, AP6; Domain Model §3 (Aggregate Roots), §9–§10 (Relationship Types); DECISION_FREEZE.md §Technology Principles

---

## Context

The Decision Graph is the core product (ADR 0002). The architecture needed to decide how to persist this graph — specifically, which storage paradigm to use as the **canonical write model** (the single source of truth).

Three options were evaluated:

### Option A — Native Graph Database (e.g., Neo4j, Amazon Neptune)

- **Pro:** Graph traversal is a first-class operation; relationships are stored natively
- **Con:** Less mature tooling for ACID transactions, audit history, and version lineage
- **Con:** Introduces operational complexity for a V1 product targeting 50–500 employee organizations
- **Con:** The ICP does not require graph-scale traversal performance in V1

### Option B — Document Store (e.g., MongoDB, Firestore)

- **Pro:** Flexible schema, fast iteration
- **Con:** Relationships are not first-class; joins and referential integrity must be managed in application code
- **Con:** Weakens traceability and auditability — violates Product Constitution Principle 4
- **Con:** Schema flexibility works against the disciplined domain model

### Option C — Relational Database with Graph Semantics through Typed Relationships

- **Pro:** Strong referential integrity, ACID transactions, mature audit/versioning patterns
- **Pro:** Relationships modeled as associative and junction tables with typed edges — preserving graph semantics in relational form
- **Pro:** Right-sized for the ICP's scale requirements (NFR-06)
- **Pro:** Well-understood operational model for a small team
- **Con:** Graph traversal requires multi-table joins rather than native graph operations

## Decision

**Use a relational database as the canonical persistence model, with graph semantics expressed through typed relationship tables.**

The schema design defines 25 logical tables across 3 layers:

| Layer | Purpose | Tables |
|-------|---------|--------|
| Reference & Tenancy | Shared/Organization-scoped data | organization, person, regulation |
| Workflow Entities | Aggregate Roots and child Entities | meeting, decision, evidence, assumption, risk, obligation, resolution, action_item, minutes + 2 Value Object collections |
| Relationship Layer | Typed edges realizing the Domain Model's 14 Relationship Types | decision_vote, decision_approval + 9 junction tables |

Key design patterns:

- **Standard audit columns** on every table (created_at, created_by_person_id) per NFR-01
- **Version lineage columns** (version_number, supersedes_id, is_current, superseded_at) on versioned entities per NFR-02
- **Organization-scoped tenancy** enforced through foreign keys per NFR-03
- **Surrogate primary keys** for all entities, with business identity rules from Domain Model §14

The relational model is the **single source of truth** (AP1). Where performance or retrieval requires a different shape — such as pre-joined rationale bundles for AI Retrieval or full-text/semantic indexes — those are built as **derived read models** that can be regenerated from the canonical model (AP6).

## Consequences

### Positive

- **Referential integrity guaranteed** — foreign keys enforce relationship constraints at the database level
- **Audit and versioning native** — version lineage and audit columns are standard relational patterns
- **Traceability by default** — every record carries creator, timestamp, and relationship edges
- **Operational simplicity** — relational databases are well-understood; no specialized graph DB ops needed for V1
- **Technology neutrality** — the logical schema is database-engine independent (AP8)

### Negative

- **Graph traversal cost** — multi-hop queries (e.g., "show all decisions linked to this regulation through any path") require multi-table joins; if performance becomes an issue post-V1, a derived graph index can be added without changing the canonical model
- **Schema rigidity** — adding new relationship types requires schema migration (but this is governed by the Decision Freeze, so ad-hoc additions are not permitted anyway)

### Neutral

- The decision to use derived read models (AP6) means a graph database, search index, or vector store can be added later as a read-only layer without architectural change — the canonical relational model remains authoritative
