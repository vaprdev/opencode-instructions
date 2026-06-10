---
name: grill-with-docs
description: Stress-test a software plan against the codebase, domain language, CONTEXT.md, and ADRs. Use when the user asks to grill, challenge, or clarify a design before implementation.
---

# Grill With Docs

Adapted for OpenCode from Matt Pocock's `grill-with-docs` skill.

Interview the user until the plan is precise enough to implement. Walk the decision tree one dependency at a time. Ask exactly one question per turn, include your recommended answer and reasoning, and wait for the user's response.

Do not ask the user questions the repository can answer. Explore the code, tests, `CONTEXT.md`, `CONTEXT-MAP.md`, and `docs/adr/` first. Treat existing documentation as evidence, not unquestionable truth; surface conflicts between docs, code, and the user's statements.

## Domain Language

- Call out terms that conflict with the project's glossary.
- Replace vague or overloaded language with a proposed canonical term.
- Test domain relationships with concrete scenarios and edge cases.
- If the repository has multiple contexts, use `CONTEXT-MAP.md` to identify the relevant context. Ask only if ownership remains ambiguous after exploration.

When a domain term is resolved, update the relevant `CONTEXT.md` immediately. Create it lazily if needed. Keep it a glossary, not a specification or implementation diary:

```md
**Canonical term**:
One or two sentences defining what the term is.
_Avoid_: ambiguous synonym, overloaded synonym
```

Include only project-specific domain concepts. Prefer one canonical term, tight definitions, and explicit avoided synonyms.

## Decisions

Offer an ADR only when the decision is all three:

1. Meaningfully expensive to reverse.
2. Surprising to a future reader without context.
3. The result of a genuine trade-off between plausible alternatives.

If accepted, create the ADR immediately under the applicable `docs/adr/` directory. Increment the highest four-digit prefix and use `NNNN-short-slug.md`. Keep the default format brief:

```md
# Short decision title

One to three sentences describing the context, decision, and reason.
```

Add status, alternatives, or consequences only when they preserve information a future reader will need.

## Boundaries

- Continue until dependencies, failure cases, ownership, data flow, rollout, and verification are resolved or explicitly out of scope.
- Record conclusions as they crystallize; do not batch documentation updates at the end.
- Do not implement the plan during the grilling session unless the user explicitly ends the interview and asks for implementation.
