# Context protocol

Every task starts from an explicit context bundle. Context is an input with an access boundary, not an implicit property of a conversation or workstation.

## Required fields

- Objective and non-goals.
- Constraints and authority.
- Evidence items with a claim and a reference.

## Optional fields

- Open decisions, risk, prior result, affected boundaries, and time budget.

## Rules

1. Supply only the context needed for the next decision or action.
2. Label evidence as direct observation, supplied assertion, or inference.
3. Do not infer new access from a reference. The consumer decides whether it can open a referenced artifact.
4. When input is insufficient, return a decision request or incomplete result; do not invent hidden context.
5. Update the compact current state after a meaningful decision so a later owner can continue without replaying raw history.

Use [context-bundle.schema.json](../schemas/context-bundle.schema.json) for a machine-readable form.
