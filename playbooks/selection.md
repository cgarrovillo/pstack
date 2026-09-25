# Task selection

Choose one primary task shape. A secondary playbook may supply a clearly named sub-step, but it must not silently change the objective or authority.

When [PStack Mode](../protocols/pstack-mode.md) is active, it performs this selection on every non-casual turn and keeps the chosen playbook as the primary task contract. Supporting routing roles add implementation, investigation, comparison, or criticism; they do not replace the primary playbook.

| If the objective is to… | Use | Primary proof |
| --- | --- | --- |
| Correct a known wrong behavior | [bug-fix](bug-fix.md) | The original reproduction passes on the same surface. |
| Add or change a promised behavior | [feature](feature.md) | The stated outcome is observed through its public boundary. |
| Change structure while preserving behavior | [refactoring](refactoring.md) | A pinned behavior contract remains equivalent. |
| Explain an unknown symptom or decision | [investigation](investigation.md) | Evidence eliminates alternatives or records an unresolved gap. |
| Improve a measured cost | [performance](performance.md) | The same measurement method shows an improvement against baseline. |
| Compare possible designs cheaply | [prototype](prototype.md) | A declared selection rule chooses or rejects an option. |
| Resume interrupted work safely | [continuation](continuation.md) | Current state, remaining risk, and next action are re-established. |

If none fits, write a new task contract before acting: objective, non-goals, inputs, evidence, authority, stop condition, and result shape. Do not use an unclear label as permission to broaden scope.
