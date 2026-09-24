# Refactoring

Use this when structure changes but observable behavior is intended to remain the same.

## Inputs

- The behavior contract to preserve.
- A current observation, characterization, or equivalence harness.
- The target structural improvement and boundaries.

## Procedure

1. Pin the current behavior before moving structure. A build-only check is not a behavior pin.
2. Name the structural problem: duplicated rule, invalid state, hidden ownership, needless layer, or obsolete path.
3. Describe the target as if the current requirement were foundational.
4. Delete obsolete code and unnecessary indirection before adding new shape.
5. Move in small, behavior-preserving units. Migrate all callers and remove the obsolete path in the same wave.
6. Check equivalence through the pinned behavior contract after each meaningful unit and inspect whether reader load actually decreased.

## Stop conditions

Split the work when a discovered defect or new behavior changes the contract. Revert the structural change if it does not reduce a named cost or risk.

## Result contract

Record: preserved behavior, structural change, equivalence proof, reader-load improvement, and intentionally excluded behavior changes.
