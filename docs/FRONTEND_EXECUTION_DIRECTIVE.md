# Frontend Execution Directive

**Document:** FRONTEND_EXECUTION_DIRECTIVE.md

**Version:** 1.0

**Status:** Active

**Approved By:** Venture Foundry OS

---

# Purpose

This document authorizes and governs the complete frontend implementation of BoardMemory Version 1.

The research, opportunity discovery, signal extraction, category discovery, stress testing, product strategy, architecture, domain modelling, database schema, API contracts and implementation governance have all been completed.

The frontend implementation phase is therefore an execution problem—not a product design problem.

The frontend engineering agent is responsible for faithfully implementing the approved architecture while producing an exceptional enterprise user experience.

This document replaces phased implementation prompts with a single execution directive.

---

# Project Status

The following work has already been completed and approved.

✓ Company Thesis

✓ Category Thesis

✓ Founder Thesis

✓ Product Constitution

✓ Decision Freeze

✓ Product Philosophy

✓ Product Scope

✓ Founder Narrative

✓ Product Requirements Document

✓ Domain Model

✓ Database Schema

✓ System Architecture

✓ API Contract Specification

✓ Implementation Rules

✓ Implementation Roadmap

The architecture is frozen.

Do not redesign it.

---

# Canonical Repository

The GitHub repository is the single source of truth.

All implementation must be performed within the repository.

Do not replace the repository.

Do not restructure the repository.

Do not create a competing architecture.

Preserve the existing project organisation.

---

# Repository Governance

Treat the following directories as read-only unless explicitly instructed otherwise.

```
docs/
.agents/
```

Do not rewrite documentation.

Do not rewrite architecture.

Do not modify governance documents.

Implementation must conform to the architecture—not the other way around.

---

# Required Reading Order

Before writing any code, complete the following sequence.

## Step 1

Read:

```
.agents/AGENTS.md
```

Understand the repository's AI operating model.

---

## Step 2

Read:

```
.agents/skills/_foundation/using-agent-skills/
```

This is the master orchestration layer.

It defines how every other skill is selected and applied.

Do not skip this step.

---

## Step 3

Load the remaining required skills as directed by the orchestration framework.

Apply only the skills necessary for implementation.

Do not ignore the foundation layer.

---

## Step 4

Read the architecture.

The following document precedence is mandatory.

1. PRODUCT_CONSTITUTION.md

2. DECISION_FREEZE.md

3. Strategic Foundation

4. Founder Narrative

5. PRD

6. Domain Model

7. Database Schema

8. System Architecture

9. API Contracts

10. IMPLEMENTATION_RULES.md

11. IMPLEMENTATION_ROADMAP.md

Higher-level documents always override lower-level documents.

---

# Mission

Implement the complete BoardMemory frontend.

Not a prototype.

Not wireframes.

Not mockups.

A production-quality frontend ready to connect to the backend.

---

# Frontend Philosophy

BoardMemory is not a document management system.

BoardMemory is not a board portal.

BoardMemory is an Enterprise Decision Memory platform.

Every design decision should reinforce that identity.

Users should feel they are exploring institutional memory—not browsing files.

The interface should communicate:

• clarity

• confidence

• trust

• governance

• relationships

• permanence

• connected knowledge

The frontend should be visually memorable without sacrificing enterprise usability.

---

# Visual Direction

Avoid conventional enterprise dashboards dominated by tables and forms.

Avoid generic SaaS aesthetics.

Avoid visually flat interfaces.

Instead, create an interface that feels:

Modern

Spatial

Immersive

Cinematic

Elegant

Responsive

Purposeful

Relationship-first

Motion should communicate information—not merely decorate the interface.

Depth should improve comprehension.

Animation should reinforce hierarchy, relationships and navigation.

The experience should leave a memorable first impression.

The Decision Graph should be treated as the visual centrepiece of the application.

It should feel closer to navigating a living constellation of organisational knowledge than browsing static records.

---

# Technical Freedom

You may choose the frontend technologies, component architecture and animation techniques that best satisfy these objectives.

Technology choices should prioritise:

Maintainability

Performance

Accessibility

Developer experience

Production readiness

Avoid unnecessary complexity.

---

# Implementation Scope

Implement the entire frontend defined by the approved architecture.

Including:

Application Shell

Authentication UI

Dashboard

Meeting Management

Decision Capture

Decision Graph

Search & Retrieval

Document Generation UI

Audit & Governance UI

Administration UI (if included in the approved architecture)

Settings

Responsive layouts

Accessibility

Component library

Navigation

Empty states

Loading states

Error handling

Client-side state

Frontend routing

Typed API clients

Mock adapters where backend services are not yet available.

---

# Backend Boundary

Backend implementation is outside your responsibility.

Do not implement:

Database logic

Authentication services

Business rules

Persistence

API redesign

Schema redesign

Graph algorithms

Infrastructure

Server-side processing

Use typed mock services where required.

Assume a backend engineer will later replace those adapters without changing the frontend.

---

# Architectural Constraints

Do not:

Change workflows

Rename domain objects

Invent new product concepts

Expand product scope

Modify APIs

Modify schemas

Rewrite documentation

Redesign governance

The architecture is frozen.

---

# Quality Standard

The frontend should be production quality.

Requirements:

Reusable components

Modular architecture

Responsive design

Accessibility

Consistent design language

Maintainable code

Strong TypeScript practices

Clear folder structure

Readable code

Minimal duplication

---

# Git Workflow

Work entirely within the existing repository.

Preserve commit history.

Group commits logically by capability.

Avoid unrelated file modifications.

Leave the repository in a buildable state.

---

# Completion Criteria

Implementation is complete when:

✓ All approved frontend capabilities are implemented.

✓ API contracts remain unchanged.

✓ Repository structure preserved.

✓ Documentation preserved.

✓ Architecture faithfully implemented.

✓ Responsive behaviour verified.

✓ Accessibility maintained.

✓ Frontend builds successfully.

✓ Backend integration points clearly defined.

✓ Application is ready for backend implementation.

---

# Deliverables

Upon completion provide:

1. Summary of implementation.

2. Repository changes.

3. Components created.

4. Routes created.

5. Mock services created.

6. Any architectural assumptions.

7. Remaining backend work for Devin.

8. Any implementation risks discovered.

9. Preview of the completed frontend.

Then stop.

Do not continue into backend implementation.
