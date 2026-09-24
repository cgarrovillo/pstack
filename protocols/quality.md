# Quality protocol

Quality is established by direct evidence that matches the promised outcome.

## Verification ladder

1. Check structure: required files, shapes, and declared invariants.
2. Check behavior: exercise the same public boundary that the affected person or system uses.
3. Check regression: prove the original failure is absent or the preserved contract still holds.
4. Check scope: inspect the final result for unrequested behavior, authority expansion, and stale paths.

## Evidence rules

- A successful build, parse, or review is supporting evidence, not sufficient behavior proof by itself.
- Use the same measurement method before and after a performance change.
- State an inconclusive result plainly. It is not a pass.
- Preserve enough evidence for another person to repeat the relevant check.

## Completion rule

Declare completion only when the result satisfies the explicit acceptance criteria, remaining risk is named, and the recorded evidence directly supports the claims made.
