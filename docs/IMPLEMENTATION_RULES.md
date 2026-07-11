# IMPLEMENTATION_RULES
# BoardMemory Implementation Rules

Version: 1.0
Status: Active
Approved By: Venture Foundry OS
Last Updated: YYYY-MM-DD

---

# Purpose

This document defines the mandatory rules governing implementation of BoardMemory.

The architecture has been completed and approved.

The implementation phase is **not** an opportunity to redesign the product.

The responsibility of implementation is to faithfully realize the approved architecture.

These rules apply equally to:

- Human developers
- AI coding agents
- External contributors
- Future engineering teams

No implementation decision may violate the Product Constitution or the Decision Freeze.

---

# Guiding Principle

**Implement the architecture.**

Do not reinterpret it.

Do not optimize it away.

Do not silently redesign it.

If implementation reveals a genuine architectural issue, pause implementation and submit it for Governance Review.

---

# Governance Hierarchy

When implementation guidance conflicts, the following order takes precedence.

1. PRODUCT_CONSTITUTION.md
2. DECISION_FREEZE.md
3. Strategic Foundation Document
4. Founder Narrative
5. Product Requirements Document (PRD)
6. Domain Model
7. Database Schema
8. System Architecture
9. API Contract Specification
10. IMPLEMENTATION_RULES.md

Lower-level artifacts must never override higher-level ones.

---

# Core Rules

## Rule 1 — Strategy Is Frozen

Implementation must not alter:

- Company Mission
- Category
- Product Philosophy
- Core Workflow
- Core Domain Objects
- Product Scope
- Expansion Boundary

Only the Founder may approve strategic changes.

---

## Rule 2 — Domain First

Business concepts are implemented exactly as defined in the Domain Model.

Do not rename entities.

Do not merge entities.

Do not introduce new entities without governance approval.

The Domain Model is the canonical business language.

---

## Rule 3 — APIs Follow Contracts

Frontend and backend must implement the approved API Contracts.

Do not invent operations.

Do not remove operations.

Do not redefine business semantics.

Contract changes require governance approval.

---

## Rule 4 — Database Follows Domain

The persistence layer exists to support the Domain Model.

Do not redesign tables for convenience.

Do not remove traceability.

Do not weaken referential integrity.

Performance optimizations must preserve business meaning.

---

## Rule 5 — Traceability Is Mandatory

Every significant business action must remain traceable.

Implementations must preserve:

- Creator
- Timestamp
- Modifier
- Approval history
- Decision history
- Supporting evidence
- Relationships

Auditability is not optional.

---

## Rule 6 — AI Is Never the System of Record

Artificial Intelligence assists users.

It does not replace institutional memory.

AI may:

- Retrieve
- Summarize
- Explain
- Suggest

AI may never:

- Invent organizational history
- Modify approved records
- Replace canonical data
- Become the authoritative source of truth

---

## Rule 7 — The Decision Graph Is Sacred

The Decision Graph is the core product asset.

Implementations must preserve:

- Relationship integrity
- Graph semantics
- Bidirectional traceability
- Business meaning of relationships

Relationships are business concepts—not implementation details.

---

## Rule 8 — Simplicity Wins

If multiple implementations satisfy the architecture:

Choose the simpler one.

Avoid:

- Premature optimization
- Unnecessary abstraction
- Clever implementations
- Framework-specific complexity

Simple systems are easier to govern.

---

## Rule 9 — Build Incrementally

Implementation proceeds feature by feature.

Each feature must be:

Designed

↓

Implemented

↓

Reviewed

↓

Accepted

↓

Merged

↓

Documented

↓

Released

No feature should begin before its dependencies are complete.

---

## Rule 10 — No Silent Scope Expansion

If implementation uncovers an attractive new feature:

Do not build it.

Document it.

Submit it through governance.

Await Founder approval.

Ideas discovered during implementation are not automatically approved.

---

# AI Tool Responsibilities

## Claude

Owns:

- Product documentation
- Architectural clarification
- Governance interpretation

Claude must never produce production code.

---

## Stitch

Owns:

- Design system
- Layout
- Design tokens
- Component library
- Visual language

Stitch must never redesign workflows.

---

## Lovable

Owns:

- Frontend implementation
- Forms
- Pages
- Dashboards
- Authentication UI
- Client-side interactions

Lovable must not redesign APIs or business logic.

---

## Devin

Owns:

- Backend implementation
- API implementation
- Database migrations
- Infrastructure
- Authentication backend
- Business logic

Devin must never change architecture.

Every task given to Devin must include:

- Required inputs
- Expected outputs
- Completion boundary
- Acceptance criteria

---

## CodeRabbit

Owns:

- Code review
- Security observations
- Performance suggestions
- Code quality

CodeRabbit must not redesign architecture.

---

# Repository Rules

Every Pull Request must:

- Reference an approved implementation task
- Reference the affected architectural artifact(s)
- Preserve traceability
- Include tests where appropriate
- Pass automated checks
- Pass governance review

No undocumented implementation should be merged.

---

# Documentation Rules

Implementation must keep documentation synchronized.

Changes affecting architecture require updates to:

- CHANGELOG.md
- Relevant implementation documents
- Architectural references (if approved)

Documentation is part of the implementation.

---

# Definition of Done

A feature is complete only when:

- Functional requirements are satisfied.
- Domain rules are preserved.
- API contracts are implemented.
- Traceability is maintained.
- Tests pass.
- Documentation is updated.
- Code review is complete.
- Governance review approves the implementation.

If any item is incomplete, the feature is not done.

---

# Handling Architectural Issues

If implementation reveals an architectural concern:

1. Stop implementation.
2. Document the issue.
3. Reference affected artifacts.
4. Propose options.
5. Submit for Governance Review.
6. Await Founder approval.

Do not implement speculative fixes.

---

# Prohibited Actions

The following are prohibited without explicit governance approval:

- Changing the Company Thesis
- Changing the Category Thesis
- Changing Product Philosophy
- Introducing new domain objects
- Redesigning workflows
- Changing API semantics
- Removing audit history
- Weakening traceability
- Replacing the Decision Graph
- Expanding V1 scope
- Introducing V2 features

---

# Continuous Governance

Every completed feature should answer:

✓ Does it align with the Product Constitution?

✓ Does it preserve the Decision Freeze?

✓ Does it faithfully implement the PRD?

✓ Does it preserve the Domain Model?

✓ Does it follow the Database Schema?

✓ Does it implement the System Architecture?

✓ Does it comply with the API Contracts?

Only when all answers are "Yes" should implementation proceed to production.

---

# Status

Status: ACTIVE

This document governs all implementation work for BoardMemory Version 1.

Every contributor is responsible for preserving architectural integrity throughout the implementation lifecycle.