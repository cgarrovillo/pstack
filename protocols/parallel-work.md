# Parallel work protocol

Parallel work is useful only when independent effort reduces time or improves criticism without obscuring ownership.

## Frame the work

Before assigning work, declare:

- Done predicate and required result.
- Inputs, evidence, authority, and budget.
- Partition shape: independent slices, competing approaches, or a mixture.
- Write ownership and conflict keys.
- Selection or integration rule.

## Run safely

1. Give every worker a self-contained brief and one bounded result.
2. Keep write areas disjoint. Shared mutable state has one named integrator.
3. A worker may narrow, never broaden, its authority.
4. Require a compact result: outcome, evidence, risks, and uncompleted work.
5. Treat a missing or malformed result as a coverage gap, not a pass.

## Integrate

One integrator compares results against the declared selection rule, resolves conflicts, and publishes a single canonical outcome. Independent criticism is valuable, but agreement is evidence only when reviewers had enough context and their claims are directly checked.
