# Model-routing protocol

PStack routes work by role and capability. The core decides what kind of model
seat a task needs. A host adapter decides which available model occupies that
seat and how the work is started.

This protocol restores the upstream routing design without embedding a model
vendor, model identifier, task API, configuration directory, or concurrency
mechanism.

## Inputs

A routing decision uses four inputs:

1. [The default policy](../routing/default-policy.json), validated by the
   [routing-policy schema](../schemas/routing-policy.schema.json).
2. Optional user or workspace overrides, validated by the
   [routing-overrides schema](../schemas/routing-overrides.schema.json).
3. An adapter-supplied capability catalog, validated by the
   [capability-catalog schema](../schemas/capability-catalog.schema.json).
4. The requested role, parent candidate when one exists, and any caller-owned
   fan-out count.

Catalog candidate IDs and independence groups are opaque. They may represent
models, model configurations, or another execution choice. Their meaning is
local to the adapter.

## Preserved role model

The default policy preserves every upstream configuration role. Closely
related upstream lines remain related, but each routable responsibility has a
stable key.

| Responsibility | Portable role |
| --- | --- |
| Feature implementation | `feature` |
| Behavior-preserving code change | `refactoring` |
| Defect diagnosis and correction | `bug-fix` |
| Performance correction | `perf-issue` |
| Repeated measured optimization | `hillclimb` |
| Judgment and prose | `judgment-and-prose` |
| Highest-complexity work | `hardest-tasks` |
| Code exploration and explanation | `how-explorer`, `how-explainer` |
| Evidence investigation and synthesis | `why-investigator`, `why-synthesizer` |
| Tooling, divergent, judgment, and synthesis reflection | `reflect-tooling`, `reflect-divergent`, `reflect-judgment`, `reflect-synthesizer` |
| Competing candidates and independent judging | `arena-runner`, `arena-cross-judge` |
| Parallel bounded work | `swarm-worker` |
| Competing architecture sketches | `architect-runner` |
| Adversarial review | `interrogate-reviewer` |

## Budget semantics

PStack retains the four upstream budget choices. The names are policy inputs,
not provider effort tokens.

| Budget | Portable target |
| --- | --- |
| `unlimited` | Keep the role's default reasoning tier. |
| `large` | Request `very-high`. |
| `medium` | Request `high`. |
| `small` | Request `medium`. |

Reasoning tiers are ordered `maximum`, `very-high`, `high`, `medium`, `low`.
When a candidate lacks the target tier, choose its highest tier at or below the
target, but never below the role's minimum fallback tier. Record this as a
fallback. Do not invent a provider-specific tier in the core.

## Overrides

An override may set a budget and change a role's selection mode:

- `capability-match` asks the adapter to choose from the catalog.
- `inherit-parent` selects the parent candidate after validating that it can
  satisfy the hard role constraints.
- `automatic` delegates the candidate choice to the adapter, which must still
  report the realized selection when the host exposes it.
- `pinned` supplies one or more opaque candidate IDs. For a panel, the list
  length sets the seat count unless `seat_count` explicitly replaces it.

Aliases such as `inherit-parent` and `automatic` are selection modes, not model
IDs. An adapter must not treat them as rejected candidates.

## Resolution algorithm

For each requested role:

1. Validate the policy, overrides, catalog, and role key. Reject unknown roles
   rather than silently using a general-purpose default.
2. Determine the seat count from the caller, override, pinned list, or role
   default, in that order.
3. Determine the requested reasoning tier from the role default, global
   budget, and role override, in that order.
4. Filter available catalog candidates by every required capability and the
   role's minimum reasoning tier.
5. Apply the selection mode. Preferences influence ranking but may not replace
   a required capability.
6. Apply the diversity rule across the selected seats. `prefer-distinct` and
   `prefer-different-from-parent` are best-effort preferences;
   `require-distinct` is a hard constraint.
7. If a configured candidate is unavailable, try an available candidate in
   the same independence group, then the remaining matching catalog. If the
   requested tier is unavailable, use the highest supported tier at or below
   it. Use the parent or automatic selection only when the role permits it.
8. If no candidate satisfies hard constraints, return `needs-choice` or
   `unavailable`. Never silently drop a required capability, minimum tier, or
   required independence rule.
9. Emit a decision conforming to the
   [routing-decision schema](../schemas/routing-decision.schema.json). Record
   every substitution, including runtime rejection and retry.

If a host rejects a candidate after resolution, refresh the catalog and run
the same algorithm again. Error-message parsing may help refresh the catalog,
but it is adapter behavior and cannot redefine the routing policy.

## Panels and fan-out

Panel roles carry a default seat count. A pinned candidate list may expand or
shrink it. Caller-fan-out roles let a playbook decide the worker count while
reusing one routing policy for each seat.

Arena cross-judging prefers an independence group different from the parent.
Architecture and adversarial-review panels prefer distinct groups. Repeating a
candidate is allowed when the rule is only a preference or when the work is
generation-bound; the decision must make the repetition visible.

Routing chooses seats. [The parallel-work protocol](parallel-work.md) still
owns briefs, write isolation, result contracts, criticism, and integration.

## Adapter contract

An adapter must:

1. Build a current catalog from models the user can actually select.
2. Keep provider names and concrete model identifiers in adapter-owned data.
3. Resolve and persist explicit overrides without changing the default policy.
4. Produce a routing decision before starting work and update it after any
   runtime fallback.
5. Map seats into the host's own agent, task, concurrency, and environment
   controls.
6. Preserve workspace authority and external-action gates. Routing is never an
   authorization grant.
7. Report the realized candidate, reasoning tier, independence group, and all
   substitutions to the caller.

The core never probes a host, writes home-directory configuration, starts an
agent, or retries a provider call by itself.
