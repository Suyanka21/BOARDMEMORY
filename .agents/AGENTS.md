# BoardMemory — Agent Skills System

## Overview

This directory contains **26 agent skills** organized by development lifecycle phase. These skills govern how AI coding agents think, code, plan, build, test, review, and ship when working on BoardMemory.

Every skill contains a `SKILL.md` file with YAML frontmatter (`name`, `description`) and detailed instructions. AI agents automatically discover and load skills from this directory.

---

## Skill Lifecycle

Skills are organized into 7 phases that follow the complete development lifecycle:

```
Foundation (always active)
    → Define (requirements & ideation)
        → Plan (task breakdown & context)
            → Build (implementation)
                → Verify (testing & debugging)
                    → Review (code quality)
                        → Ship (deployment & governance)
```

---

## Phase Map

### Foundation — Always Active, Never Invoked

These are not skills you trigger. They are permanent cognitive and coding layers that apply to every task, every session, without exception.

| Skill | Purpose |
|-------|---------|
| `global-reasoning-layer` | How this agent thinks at all times — correctness priority, assumption protocol, confidence calibration |
| `coderabbit-dna` | How this agent codes at all times — defensive coding, error handling, edge cases, security, self-review |
| `using-agent-skills` | Master orchestrator — skill discovery map, lifecycle sequence, audit requirements |

### Define — Pre-Build

| Skill | Purpose | Trigger |
|-------|---------|---------|
| `idea-refine` | Divergent/convergent thinking for vague ideas | "ideate", "refine this idea", "stress-test my plan" |
| `interview-me` | Extract real intent through one-question-at-a-time interview | Underspecified asks, "interview me", "grill me" |
| `spec-driven-development` | Write structured specs before writing any code | New project/feature, unclear requirements |

### Plan — Task Breakdown & Context

| Skill | Purpose | Trigger |
|-------|---------|---------|
| `planning-and-task-breakdown` | Break specs into small, verifiable tasks with acceptance criteria | Have a spec, need tasks |
| `context-engineering` | Load right project context for agent sessions | New session, quality degradation, task switching |

### Build — Implementation

| Skill | Purpose | Trigger |
|-------|---------|---------|
| `incremental-implementation` | Thin vertical slices — implement, test, verify, expand | Any multi-file change |
| `source-driven-development` | Verify against official documentation before implementing | Framework/library work |
| `frontend-ui-engineering` | Production UI with accessibility | Building/modifying user-facing interfaces |
| `api-and-interface-design` | Stable API contracts with clear boundaries | Designing APIs, module boundaries |
| `security-and-hardening` | OWASP prevention, input sanitization, auth verification | Handling user input, auth, data storage |
| `code-simplification` | Reduce complexity without changing behavior | Code works but is hard to maintain |

### Verify — Testing & Debugging

| Skill | Purpose | Trigger |
|-------|---------|---------|
| `test-driven-development` | Failing test first, then pass | Implementing logic, fixing bugs, changing behavior |
| `browser-testing-with-devtools` | Runtime verification via Chrome DevTools | Browser-based features |
| `debugging-and-error-recovery` | Reproduce → localize → fix → guard | Tests fail, builds break, unexpected errors |
| `doubt-driven-development` | Adversarial review of non-trivial decisions | High stakes, unfamiliar code, production logic |
| `performance-optimization` | Measure first, optimize what matters | Performance requirements, suspected regressions |

### Review — Code Quality

| Skill | Purpose | Trigger |
|-------|---------|---------|
| `code-review-and-quality` | Five-axis review with quality gates | Before merging any change |

### Ship — Deployment & Governance

| Skill | Purpose | Trigger |
|-------|---------|---------|
| `git-workflow-and-versioning` | Atomic commits, clean history, reversible changes | Any code change ready to commit |
| `ci-cd-and-automation` | Automated quality gates on every change | Setting up or modifying pipelines |
| `documentation-and-adrs` | Document decisions and reasoning | Architectural decisions, API changes, feature shipping |
| `deprecation-and-migration` | Remove old systems safely | Removing APIs, features, or migrating users |
| `trustless-system-auditor` | Reality-gap audit — must pass before real users | Before every deployment (mandatory, no exceptions) |
| `shipping-and-launch` | Pre-launch checklist, monitoring, rollback strategy | Preparing to deploy to production |

---

## Skill Discovery

When a task arrives, identify the phase and apply the corresponding skill:

```
Task arrives
│
├── Vague idea / need refinement?  → idea-refine
├── New project / feature / change? → spec-driven-development
├── Have a spec, need tasks?        → planning-and-task-breakdown
├── Implementing code?              → incremental-implementation
│   ├── UI work?                    → frontend-ui-engineering
│   ├── API work?                   → api-and-interface-design
│   ├── Need better context?        → context-engineering
│   └── Need doc-verified code?     → source-driven-development
├── Writing / running tests?        → test-driven-development
│   └── Browser-based?              → browser-testing-with-devtools
├── Something broke?                → debugging-and-error-recovery
├── Reviewing code?                 → code-review-and-quality
│   ├── Security concerns?          → security-and-hardening
│   ├── Too complex?                → code-simplification
│   └── Performance concerns?       → performance-optimization
├── Committing / branching?         → git-workflow-and-versioning
├── CI/CD pipeline work?            → ci-cd-and-automation
├── Writing docs / ADRs?            → documentation-and-adrs
├── Removing old systems?           → deprecation-and-migration
└── Deploying / launching?          → trustless-system-auditor
                                    → shipping-and-launch
```

---

## BoardMemory-Specific Rules

All skills operate under the BoardMemory governance framework:

1. The **Product Constitution** and **Decision Freeze** override all skill guidance
2. Skills must never expand V1 scope or introduce new domain concepts
3. The **12 Core Domain Objects** are frozen — no renaming, merging, or splitting
4. The **Core Workflow** (Meeting → Decision → Graph → Retrieval) must be strengthened, never bypassed
5. AI is the interface, never the system of record — the Decision Graph is authoritative
6. Every change must pass the **7-question Decision Test** before implementation

See the root `AGENTS.md` for the complete AI operating instructions.
