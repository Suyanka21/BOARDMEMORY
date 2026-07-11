# AGENTS.md — BoardMemory AI Operating Instructions

Version: 1.0
Status: Active
Approved By: Venture Foundry OS
Last Updated: 2026-07-11

---

## Purpose

This document defines the mandatory operating instructions for every AI system working on BoardMemory.

All AI agents — coding assistants, design tools, code reviewers, and orchestration systems — must comply with these rules.

No AI system may independently override, reinterpret, or extend these instructions.

---

## Governance Hierarchy

When guidance conflicts, the following precedence applies:

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
11. IMPLEMENTATION_ROADMAP.md
12. AGENTS.md (this document)

Lower-level artifacts must never override higher-level artifacts.

---

## Universal AI Rules

### AI Systems May

- Clarify requirements
- Improve implementation quality
- Refine documentation
- Identify implementation risks
- Suggest performance improvements
- Recommend security improvements
- Execute approved implementation tasks

### AI Systems May Not

- Change product strategy
- Expand product scope
- Introduce new workflows
- Add new domain concepts
- Redefine the category
- Alter the Decision Freeze
- Override architectural decisions without governance approval
- Introduce V2 features into V1
- Rename, merge, or split Core Domain Objects
- Redesign the Core Workflow

---

## AI Ownership Matrix

Each AI tool has a defined responsibility boundary. Work outside that boundary requires governance approval.

### Claude

**Owns:**
- Product documentation
- Architectural clarification
- Governance interpretation
- Architecture Decision Records (ADRs)
- Strategic guidance

**Boundaries:**
- Claude must never produce production code
- Claude must never alter frozen strategic decisions
- Claude interprets architecture; Claude does not create architecture

---

### Stitch

**Owns:**
- Design system
- Layout
- Design tokens
- Component library
- Visual language
- Accessibility guidelines
- Interaction principles

**Boundaries:**
- Stitch must never redesign workflows
- Stitch must never alter business logic
- Stitch must never introduce new domain concepts
- Design decisions must derive from the approved Architecture and PRD

---

### Lovable

**Owns:**
- Frontend implementation
- Forms
- Pages
- Dashboards
- Authentication UI
- Client-side interactions
- Loading, empty, and error states

**Boundaries:**
- Lovable must not redesign APIs or business logic
- Lovable must implement the approved API Contracts faithfully
- Lovable must follow the Design System created by Stitch
- Lovable must not introduce backend functionality

---

### Devin

**Owns:**
- Backend implementation
- API implementation
- Database migrations
- Infrastructure
- Authentication backend
- Business logic
- Domain Services implementation

**Boundaries:**
- Devin must never change architecture
- Devin must implement the approved API Contracts exactly as specified
- Devin must preserve all Domain Model invariants
- Devin must maintain traceability (creator, timestamp, modifier, approval history)

**Every task given to Devin must include:**
- Required inputs
- Expected outputs
- Completion boundary
- Acceptance criteria

---

### CodeRabbit

**Owns:**
- Code review
- Security observations
- Performance suggestions
- Code quality assessment
- Standards compliance

**Boundaries:**
- CodeRabbit must not redesign architecture
- CodeRabbit must not approve scope expansion
- CodeRabbit reviews against the approved architecture, not against general best practices that conflict with it

---

## Core Domain Objects (Frozen)

The following twelve objects are approved for Version 1. No object may be renamed, merged, split, or added without founder approval.

1. Decision
2. Meeting
3. Resolution
4. Person
5. Organization
6. Regulation
7. Risk
8. Assumption
9. Obligation
10. Evidence
11. Action Item
12. Relationship

---

## Core Workflow (Frozen)

```
Meeting → Discussion → Decision → Rationale → Approval → Minutes → Decision Graph → Future Retrieval
```

Every implementation must strengthen this workflow. No feature may bypass it.

---

## Product Philosophy (Immutable)

These statements define the identity of BoardMemory and must remain recognizable throughout the product:

- Documents are evidence.
- Decisions are knowledge.
- Reasoning is an organizational asset.
- AI is the interface.
- The Memory Graph is the product.

---

## Decision Test

Every proposed feature must answer "Yes" to all of the following:

1. Does it strengthen institutional memory?
2. Does it improve decision traceability?
3. Does it preserve reasoning?
4. Does it simplify the board governance workflow?
5. Does it strengthen the Enterprise Decision Memory category?
6. Does it align with the Company Mission?
7. Does it respect the Decision Freeze?

If any answer is "No", the proposal must be rejected or revised.

---

## Implementation Rules for AI

1. **Implement the architecture.** Do not reinterpret it. Do not optimize it away. Do not silently redesign it.
2. **Domain First.** Business concepts are implemented exactly as defined in the Domain Model.
3. **APIs Follow Contracts.** Frontend and backend must implement the approved API Contracts.
4. **Database Follows Domain.** The persistence layer exists to support the Domain Model.
5. **Traceability Is Mandatory.** Every significant business action must remain traceable.
6. **AI Is Never the System of Record.** The Decision Graph is authoritative; AI responses must derive from it.
7. **The Decision Graph Is Sacred.** Relationship integrity, graph semantics, and bidirectional traceability must be preserved.
8. **Simplicity Wins.** Choose the simpler implementation when multiple options satisfy the architecture.
9. **Build Incrementally.** Complete one feature before starting the next.
10. **No Silent Scope Expansion.** Document new ideas; submit through governance; await founder approval.

---

## Handling Architectural Issues

If implementation reveals an architectural concern:

1. Stop implementation.
2. Document the issue.
3. Reference affected artifacts.
4. Propose options.
5. Submit for Governance Review.
6. Await Founder approval.

Do not implement speculative fixes.

---

## Documentation Synchronization

Implementation must keep documentation synchronized.

Changes affecting architecture require updates to:
- CHANGELOG.md
- Relevant implementation documents
- Architectural references (if approved)

Documentation is part of the implementation.

---

## Definition of Done

A feature is complete only when:

- ✓ Functional requirements are satisfied
- ✓ Domain Model is preserved
- ✓ Database Schema is preserved
- ✓ API Contracts are implemented
- ✓ Tests pass
- ✓ Documentation is updated
- ✓ Code review is complete
- ✓ Governance review approves the implementation

If any item is incomplete, the feature is not done.

---

## Status

Status: **ACTIVE**

This document governs all AI operations on BoardMemory Version 1.

Every AI system is responsible for preserving architectural integrity throughout the implementation lifecycle.
