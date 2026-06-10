# Rich Hickey-Inspired Design Preferences

Use these as strong design preferences, not mechanical rules. Apply them when they make the system simpler to reason about, test, change, and operate. Preserve established project conventions unless changing them is part of the task.

## Prefer Values Over Stateful Objects

- Represent facts as immutable, inspectable values.
- Keep identity and changing state separate from the values observed at a point in time.
- Isolate necessary mutation at explicit boundaries instead of spreading it through domain objects.

## Prefer Functions And Namespaces Over Methods

- Put transformations in functions whose inputs and outputs are visible.
- Use modules or namespaces for organization rather than classes that exist only to hold methods.
- Use methods when behavior genuinely belongs to a stateful capability or an established interface, not by default.

## Prefer Managed References Over Raw Variables

- When state must change, use the ecosystem's managed reference, transaction, synchronization, or lifecycle mechanism.
- Make ownership, consistency, and update semantics explicit.
- Avoid shared mutable variables and ad hoc mutation.

## Prefer A La Carte Polymorphism

- Prefer protocols, interfaces, type classes, capabilities, or injected functions that types can adopt independently.
- Avoid inheritance hierarchies used primarily for code reuse.
- Avoid central switch statements and pattern matches that must be edited for every new variant when open, independently extensible polymorphism is the real requirement.
- Keep closed algebraic data types and exhaustive pattern matching when the domain is intentionally closed; do not replace a simple closed model with speculative extensibility.

## Prefer Data Over Syntax

- Represent rules, configuration, and domain information as plain inspectable data when data is sufficient.
- Avoid bespoke DSLs, annotation systems, fluent APIs, and object graphs that hide information behind ceremony.

## Prefer Set Functions Over Imperative Loops And Folds

- Express membership, union, intersection, and difference with set operations.
- Prefer declarative collection operations that reveal intent over accumulator plumbing.
- Use loops or folds when ordering, streaming, performance, or a true sequential dependency makes them clearer.

## Prefer Queues Over Actors

- Model ordered work and producer-consumer flow with explicit queues.
- Make backpressure, concurrency, retry, and ownership policies visible.
- Use actors only when independent identity, encapsulated state, and message-driven lifecycle are actual domain requirements.

## Prefer Declarative Data Manipulation Over ORMs

- Express querying and updates directly with SQL, Datalog, relational operations, or another declarative data language.
- Keep transaction boundaries and data shapes explicit.
- Avoid object-relational models that hide queries, generate accidental I/O, or entangle persistence with domain behavior.

## Prefer Rules Over Conditionals

- Model independent business decisions as named rules with explicit inputs and outputs.
- Compose, query, and test rules independently instead of scattering nested conditionals across the system.
- Keep a direct conditional when the decision is local and simpler than introducing a rule abstraction.
