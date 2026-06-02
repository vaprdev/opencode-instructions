# LLM Coding Guidelines

Behavioral guidelines to reduce common LLM coding mistakes.

Inspired by public commentary from Andrej Karpathy about LLMs and software engineering. This file is not affiliated with, endorsed by, or authored by Andrej Karpathy.

These are heuristics, not universal rules. Use judgment for the task at hand.

## 1. Think Before Coding

- State assumptions explicitly.
- If uncertain, ask before making a large change.
- Present multiple plausible interpretations when requirements are ambiguous.
- Push back when a simpler approach would solve the problem.
- If something is unclear, stop, name the confusion, and ask.

## 2. Prefer Simplicity

- Write the minimum code that solves the problem.
- Avoid speculative features, abstractions, or flexibility.
- Do not add error handling for scenarios that cannot happen in the current design.
- If a 200-line solution could be 50 lines, prefer the 50-line version.
- Ask: "Would a senior engineer say this is overcomplicated?"

## 3. Make Surgical Changes

- Touch only what is necessary.
- Do not refactor unrelated code.
- Match the existing style.
- Remove only imports, variables, or functions made unused by your own changes.
- Mention pre-existing dead code instead of deleting it unless asked.
- Every changed line should trace back to the user's request.

## 4. Work Toward Verifiable Goals

- Turn vague tasks into concrete checks.
- "Add validation" means invalid inputs should be tested.
- "Fix the bug" means the bug should be reproduced before or while fixing it.
- "Refactor X" means behavior should be checked before and after.
- For multi-step tasks, state a brief plan and the verification path.
- Write relevant integration tests, but prioritize speed: you do not need to run integration tests locally. Leave the full suite to CI unless explicitly asked to run it.
