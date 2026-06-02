# Effect Best Practices

Functional programming guidelines for TypeScript applications using Effect.
Keep the core declarative, typed, and composable. Use judgment at integration boundaries.

## 1. Model Programs as Values

- Treat `Effect<A, E, R>` as a lazy workflow description: success value `A`, typed recoverable errors `E`, and required services `R`.
- Compose effects first. Run them only at application boundaries.
- Prefer pure functions and immutable values. Keep mutation, I/O, time, and external state inside explicit effects.
- Prefer `Effect.gen` with `yield*` for sequential workflows and combinators for transformations, recovery, logging, retries, and spans.

## 2. Write Effect-Native Code

- Define reusable operations with named `Effect.fn("Service.method")(function* (...) { ... })` for useful traces and stack information.
- Use `Effect.fnUntraced` only intentionally for low-level or hot-path code.
- Do not use `async` / `await` or JavaScript `try` / `catch` to handle yielded Effect failures inside Effect-native code.
- Wrap throwing synchronous APIs with `Effect.try` and Promise APIs with `Effect.tryPromise`.
- Use `return yield*` for terminal generator branches such as `return yield* Effect.fail(error)`.

## 3. Define Focused Services

- Model significant capabilities as small class-based `Context.Service` services with Effect-returning operations.
- Depend on services through the Effect context instead of constructing implementations inside business logic.
- Keep interfaces focused. Split unrelated capabilities rather than creating large services.
- Replace infrastructure with test layers instead of bypassing service boundaries.

## 4. Build Dependencies with Layers

- Construct implementations with `Layer.succeed`, `Layer.sync`, or `Layer.effect` according to whether construction is immediate, lazy synchronous, or effectful.
- Use `Layer.provide` when dependencies are implementation details that should be hidden.
- Use `Layer.provideMerge` only when both a service and its dependencies should remain available.
- Use `Layer.mergeAll` for independent layers. Wire the full application layer at the composition root.

## 5. Validate Boundaries with Schema

- Decode untrusted input at boundaries with `Schema.decodeUnknownEffect` so validation failures stay in the typed error channel.
- Use `Schema.Class` or `Schema.Struct` for data that needs runtime validation, encoding, or reusable structure.
- Represent expected domain failures as tagged typed errors, not thrown exceptions.
- Use `Schema.TaggedErrorClass` when an error also needs schema-based encoding, decoding, transport, or persistence.
- Recover narrowly with `Effect.catchTag` or `Effect.catchTags`. Translate infrastructure failures into domain failures with `Effect.mapError`.

## 6. Manage Lifecycle Explicitly

- Use `Effect.acquireRelease` for scoped resources and `Effect.acquireUseRelease` for local bracketed operations. Prefer structured cleanup over manual finalizers.
- Tie background work to its owner with `Effect.forkScoped`. Detach fibers only when lifecycle ownership is intentionally external.
- Express parallel work with `Effect.all` and `Effect.forEach`; choose concurrency bounds deliberately instead of using ad hoc Promise orchestration.
- Use `Clock` for time-dependent logic so tests can use virtual time.

## 7. Keep Execution at the Edge

- Keep core logic Effect-native. Adapt frameworks, callbacks, and legacy APIs at thin integration boundaries.
- Use a `ManagedRuntime` built from the application layer when non-Effect code needs to execute Effect programs.
- Test programs as Effects with test layers and virtual time where relevant.
