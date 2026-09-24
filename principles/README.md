# Principles

These rules are intentionally short. They guide judgment; they do not grant authority or replace evidence.

## Scope and shape

1. Prefer deletion and the smallest change that solves the evidenced problem.
2. Choose data structures, invariants, and ownership boundaries before adding logic.
3. Design toward the intended end state instead of preserving temporary compatibility paths.
4. When several fixes fail on the same assumption, investigate the assumption before adding another patch.
5. Subtract dead weight, redundant checks, and stale references before adding new structure.
6. Reduce reader load: collapse unnecessary layers, duplicate decisions, and hidden mutable state.
7. Build toward a named outcome; do not optimize a temporary intermediate state that must be discarded.
8. Prefer the experience of the affected person over implementation convenience.
9. Compare competing prototypes when a design choice is uncertain.
10. Build a repeatable lever for repeated work, measurement, or verification.

## Domain and boundaries

11. Represent the domain in explicit structures rather than scattered branches.
12. Validate at external boundaries and keep internal logic focused on the domain rules it owns.
13. Make invalid states difficult or impossible to represent.
14. Design repeatable operations to converge safely after partial progress.
15. Migrate callers and remove obsolete paths in the same intentional change.
16. Divide shared mutable state before serializing access to it; serialize only for a real invariant.

## Verification

17. Check the real artifact, not a proxy, self-report, or compilation alone.
18. Reproduce a symptom and trace its mechanism before treating a hypothesis as a fix.
19. Sequence work into small units that each end with direct evidence.
20. Test observed behavior through the public boundary, not incidental details.

## Collaboration and learning

21. Keep working context compact, explicit, and sufficient for the next owner.
22. Make safe progress without waiting; reserve a decision request for an irreversible or authority-expanding action.
23. Encode a durable lesson in structure, validation, or a repeatable check rather than relying only on remembered prose.

Use a principle only when its evidence condition holds. A principle never overrides safety, a stated constraint, or an explicit authority boundary.
