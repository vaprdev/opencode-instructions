# Simplicity Principles

Software design guidelines inspired by Rich Hickey's public talks and writing, especially ideas from "Simple Made Easy" and the Clojure philosophy.

This file is not affiliated with, endorsed by, or authored by Rich Hickey.

These are heuristics, not universal rules. Use judgment for the task at hand.

## 1. Prefer Simple Over Easy

- Simple means one role, one concept, and minimal interleaving.
- Easy means familiar, nearby, or convenient.
- Choose simple when possible. Easy choices today often create complexity later.

## 2. Treat Simplicity as a Reliability Tool

- Complex systems are harder to reason about, test, and change.
- If a design cannot be held in your head, simplify it.
- Reduce complexity before adding mechanisms to manage it.

## 3. Keep Concerns Separate

- Do not braid together things that can vary independently.
- Keep state separate from logic where practical.
- Keep I/O separate from computation where practical.
- Prefer pure functions and immutable data for core logic.

## 4. Compose Small Parts

- Build systems from focused pieces with clear roles.
- Compose simple components rather than creating large objects or frameworks.
- Avoid god objects, deep inheritance trees, and implicit global state.

## 5. Prefer Values Over Mutable Places

- Values are easier to inspect, compare, pass around, and reason about.
- Mutable places entangle meaning with time.
- If state must change, isolate mutation and make it explicit.

## 6. Keep Data Visible

- Prefer plain data when plain data is enough.
- Avoid hiding information behind unnecessary classes, getters, setters, or protocols.
- Let information flow through the system in inspectable forms.

## 7. Use the Right Simple Tool

| Concept | Prefer | Be Careful With |
|---|---|---|
| Values | Immutable values and persistent data structures | Mutable objects whose meaning changes over time |
| Functions | Stateless functions and methods | Behavior that depends on hidden state, globals, time, or I/O |
| Namespaces | Modules and language-level namespaces | Huge classes used only for organization |
| Data | Maps, arrays, sets, JSON, XML, records | Over-modeled objects that trap data behind behavior |
| Polymorphism | Explicit protocols, interfaces, or type classes | Deep inheritance trees created only to share behavior |
| State | Controlled references and transactions | Random mutable state spread across the system |
| Sets | Standard union, intersection, difference, and membership operations | Hand-rolled loops that hide set intent |
| Queues | Explicit queues for ordered work | Shared mutable arrays pretending to be queues |
| Queries | Declarative data manipulation | Imperative nested loops for filtering and joining data |
| Rules | Clear independent business rules | Scattered conditionals across unrelated modules |
| Consistency | Transactions and immutable snapshots | Partial updates and observable halfway states |
