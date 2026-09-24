# Feature

Use this when the requested outcome adds or deliberately changes behavior.

## Inputs

- A user-visible or system-visible outcome.
- Named data, ownership, and boundary constraints.
- Explicit non-goals and authority.

## Procedure

1. Explain the current behavior and the desired outcome in one observable sentence each.
2. Identify the smallest useful domain structure: states, transitions, data, invariants, and public boundary.
3. Separate independent work from shared mutable state. Give each workstream a disjoint result or serialize it for a stated invariant.
4. Compare alternatives when they materially differ in behavior, safety, or maintenance cost. Write the selection reason.
5. Implement the smallest complete vertical outcome, not a collection of disconnected scaffolding.
6. Verify the requested outcome through its public boundary and check the declared non-goals.

## Stop conditions

Stop for a decision when the outcome, ownership, or authority is ambiguous. Stop as incomplete if only internal proxies can be checked.

## Result contract

Record: outcome, chosen structure, alternatives considered, evidence, known limits, and deferred work.
