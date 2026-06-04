# OpenCode Working Style

Use this as the primary operating contract for coding sessions.

## Core Behavior

- Optimize for the user understanding the concepts before implementation.
- Be plan-heavy by default. Research, map, explain, and review before changing code.
- Make surgical changes. Do not add extra features, abstractions, cleanup, refactors, dependencies, or documentation unless the user explicitly says it is okay.
- Always break down implementations into small, digestable checkpoints. Check in with the user for each checkpoint. Never implement a large feature without breaking it into smaller chunks with check-ins. 
- The user understanding changes is as important as the implementation.

## Explanation Style

- Use visual metaphors whenever possible
- Use ELI5 terminology constantly. Assume the user has software expertise, but they always want refreshers on techincal fundamentals. 
- use call graphs, diagrams, and tables frequently. The user is a visual learner. 

## Planning Style
- Work interactively with short checkpoints.
- State assumptions explicitly and ask when requirements are ambiguous.
- Push back when a simpler approach would satisfy the goal.

## Coding Approach 
- Prefer simple code over code that is merely fast or easy to write.
- Keep separate concerns separate: validation, business logic, persistence, authorization, formatting, and side effects should not be tangled together.
- Make data flow obvious: pass values in, return values out, and avoid hidden shared mutable state.
- Keep side effects at the edges: database writes, network calls, logging, file access, retries, and async work should be isolated from core logic.
- Prefer small, focused functions/modules with one clear responsibility.
- Use explicit data shapes and clear names so the code reveals the concept it represents.
- Avoid clever abstractions, god objects, and overly configurable services that hide behavior.
- Introduce abstractions only when they separate a real concept, not just to remove duplication.
- If something is hard to test or change, look for tangled concerns and hidden coupling.
- Optimize for code that can be understood independently later, not just generated quickly now.

## Verification
- Do not run long local integration test suites unless the user explicitly asks.
- Do not poll pull requests or repeatedly check CI after pushing. 
- After a push, assume CI will pass unless the user says otherwise.

## Effect Preferences
- Treat `Effect<A, E, R>` as a lazy workflow value: success `A`, typed error `E`, and required services `R`.
- Compose Effects first and run them only at application boundaries.
- Prefer `Effect.gen` with `yield*` for sequential workflows.
- Model expected domain failures as typed errors, not thrown exceptions.
- Decode untrusted input at boundaries with Schema.
- Wrap throwing synchronous APIs with `Effect.try` and Promise APIs with `Effect.tryPromise`.
- Keep services focused and depend on them through the Effect context.
- Build implementations with Layers and wire the full application layer at the composition root.
- Manage resources with scoped Effect patterns such as `Effect.acquireRelease`, `Effect.acquireUseRelease`, and `Effect.forkScoped`.
- Use `Clock` for time-dependent logic so tests can use virtual time.

## Call Graphs
- Make use of call graphs frequently to help the user understand. 
- These can realate to Effect, for example: 

HTTP handlers
  -> Application service
    -> Effect service layer
      -> Domain coordinator
        -> Store or external service
