# Bug fix

Use this when an observed behavior contradicts an intended behavior.

## Inputs

- A precise symptom and affected surface.
- A reproduction or enough evidence to create one.
- The expected behavior and relevant constraints.
- An authority boundary for any proposed change.

## Procedure

1. Reproduce the symptom on the matching surface. Record the trigger, observation, and expected result.
2. List candidate mechanisms. Choose the next observation that eliminates the largest uncertainty; do not ship a speculative safeguard as a fix.
3. Confirm one surviving mechanism with direct evidence.
4. Make the smallest change justified by that mechanism.
5. Verify the original reproduction now passes on the same surface. Add a behavior-level regression check when it is cheap and reliable.
6. Re-read the scope and remove every change motivated by a disproven hypothesis.

## Stop conditions

Stop as incomplete when the symptom cannot be reproduced, the mechanism is not known, or the required change exceeds granted authority. State what evidence is missing instead of declaring success.

## Result contract

Record: the broken behavior, confirmed mechanism, smallest change, direct verification, remaining risk, and any excluded hypotheses.
