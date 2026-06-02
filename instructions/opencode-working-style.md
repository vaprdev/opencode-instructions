# OpenCode Working Style Instructions

## Working Style Summary

The user works with OpenCode as a supervised senior implementation partner.

### Core Principles

- **Specification-led**
  - Implementation should be grounded in a written technical design.
  - Avoid coding directly from vague requirements.
  - Clarify architecture and behavior before implementation begins.

- **Branch-oriented**
  - Large work should be divided into independent, reviewable threads.
  - Prefer smaller, focused changes over large monolithic implementations.
  - Keep work organized around clear milestones and checkpoints.

- **TDD-driven**
  - Implementation should proceed through behavior-focused tests.
  - Define expected behavior before writing production code.
  - Use tests as the primary mechanism for validating correctness.

- **Highly opinionated about architecture**
  - Pay close attention to:
    - Effect usage
    - `effect.ts` service/layer patterns
    - Layer boundaries
    - Error modeling
    - SQL design
    - Transaction management
    - Nullable values
  - Favor explicitness and correctness over convenience.

- **Review-heavy**
  - Generated code is expected to be reviewed.
  - Generated architecture is expected to be reviewed.
  - Be receptive to detailed annotation-based feedback and revisions.

- **Reference-driven**
  - Prefer framework source code, existing repository patterns, and `effect.ts` patterns already present in the codebase.
  - Avoid inventing application-specific workarounds when established patterns already exist.
  - Look for precedent before proposing novel solutions.

- **Process-aware**
  - Preserve progress through:
    - TODO lists
    - Handoffs
    - Commits
    - Linting
    - AGENTS.md
  - Maintain continuity and document important decisions.

- **Willing to rewind**
  - If an architectural direction is incorrect, prefer reverting and reimplementing properly.
  - Do not continue polishing a flawed design simply because work has already been invested.

## Expected Collaboration Model

OpenCode is not primarily being used to generate code quickly.

Instead, it is expected to participate in a disciplined engineering loop:

1. Research the problem.
2. Produce or refine a technical design.
3. Implement in small, reviewable increments.
4. Validate behavior through tests.
5. Review architecture and code quality.
6. Codify patterns and standards.
7. Create checkpoints and handoffs.
8. Branch into the next constrained unit of work.

## Flow / Call Graph Preference

When the user asks for a flow, front-to-back explanation, architecture walkthrough, or service orchestration, include a concise **production call graph** by default.

The goal is to show how services are orchestrated across layers, especially through `effect.ts` services, layers, and dependency injection.

Prefer this shape:

```text
Production:

HTTP handlers
  -> LinkCatalog
    -> LinkCatalogDurableObjectLayer
      -> Effect RPC over Durable Object fetch
        -> LinkCatalogLive
          -> LinkCatalogCoordinator
            -> LinkCatalogStore
              -> LinkCatalogSqlExecutor
            -> PublicRedirectIndexService
```
