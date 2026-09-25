# PStack Mode protocol

PStack Mode is the portable dispatcher for nontrivial work. Once activated in
a declared scope, it evaluates every later turn, selects a playbook when one
fits, adds supporting routing roles when rigor calls for them, and otherwise
passes the turn through unchanged.

Sticky means that activation survives a handled turn. It does not mean that a
background process runs, that work continues without an event, or that the
mode acquires new authority.

## State

An adapter persists [mode state](../schemas/mode-state.schema.json) in an
explicit conversation, workspace, session, or adapter-defined scope. It loads
that state before classifying each turn and writes the next state after the
decision.

The state records:

- whether PStack Mode is active;
- how it was activated and where it persists;
- whether the user explicitly opted out;
- the last turn's classification, action, playbook, and routing roles;
- references to the routing decisions used for that turn.

No hidden session assumption is part of the core. If an adapter cannot persist
state, it must require explicit activation for each turn and disclose that the
mode is not sticky in that environment.

## Turn classifier

Evaluate a turn in this order:

1. **Explicit control.** Activation enables the mode. An explicit opt-out or
   disable request records `opted_out: true`, sets the mode to `inactive`, and
   takes no task action beyond acknowledging the change.
2. **Inactive state.** When inactive, take no dispatch action until activation.
3. **Casual turn.** Conversation that neither matches a playbook nor needs
   engineering rigor passes through. The mode remains active.
4. **Primary task shape.** Match exactly one primary playbook using
   [task selection](../playbooks/selection.md). Record the selected playbook.
5. **Supporting rigor.** Add routing roles required by the work's shape. These
   roles support the primary playbook; they do not silently replace it or
   broaden authority.
6. **Dispatch.** Resolve every role through the
   [model-routing protocol](model-routing.md), execute through the adapter, and
   retain one canonical outcome according to the applicable protocol.
7. **Persist.** Record the classification and routing-decision references. The
   mode remains active for the next turn unless the user opted out.

When no bundled playbook fits a nontrivial task, write a task contract with an
objective, non-goals, inputs, evidence, authority, stop condition, and result
shape before dispatching it. Record the classification as `rigor` rather than
pretending a near match is exact.

## Primary playbook routing

| Turn intent | Primary playbook | Initial routing role |
| --- | --- | --- |
| Correct known wrong behavior | `bug-fix` | `bug-fix` |
| Add or change behavior | `feature` | `feature` |
| Preserve behavior while changing structure | `refactoring` | `refactoring` |
| Explain runtime shape or historical motivation | `investigation` | `how-explorer` or `why-investigator`, followed by its synthesizer role |
| Improve a measured cost | `performance` | `perf-issue` |
| Compare possible designs cheaply | `prototype` | `arena-runner`, then `arena-cross-judge` |
| Resume interrupted work | `continuation` | Select from the remaining task after reconstructing state. |

## Supporting rigor triggers

Add supporting roles when their trigger is present:

- Work that crosses a meaningful boundary or changes ownership uses
  `architect-runner` before implementation.
- A contested design or high-risk review uses `interrogate-reviewer`.
- Independent slices, coverage, or a race use `swarm-worker`.
- Competing whole designs use `arena-runner` and `arena-cross-judge`.
- Difficult cross-cutting, concurrent, or algorithmic work uses
  `hardest-tasks`.
- User-facing prose or a judgment-heavy synthesis uses
  `judgment-and-prose`.

Do not add fan-out merely because a host supports it. The task must benefit
from independent context, coverage, competition, or criticism.

## State transitions

| Current state | Event | Action | Next state |
| --- | --- | --- | --- |
| Inactive | Activate | Record activation. | Active |
| Active | Casual turn | Pass through. | Active |
| Active | Matching task | Select, route, and dispatch. | Active |
| Active | Nonmatching rigorous task | Write a task contract, route, and dispatch. | Active |
| Active | Explicit opt-out | Deactivate and record opt-out. | Inactive |
| Inactive and opted out | Activate again | Clear opt-out and record activation. | Active |

## Adapter contract

An adapter provides the entry point and persistence mechanism. It may expose a
command, skill, configuration switch, workspace policy, or other interface.
The core requires only equivalent observable behavior:

- activation is explicit or declared by workspace policy;
- active state is reloaded before every turn in scope;
- casual turns remain undisturbed;
- nontrivial turns receive one primary task contract;
- routing decisions are visible and provider-neutral at the core boundary;
- opt-out takes effect before task dispatch;
- permissions and external-action approvals remain owned by the host.

A host-specific reminder, mode flag, scheduler, or background-task API may
implement this contract, but none is required by it.
