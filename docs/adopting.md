# Adopting the portable core

PStack is designed to be read directly or translated by another environment. The environment owns every operational decision: identity, permissions, context retrieval, execution, storage, review submission, and external writes.

## Safe adapter contract

An adapter should:

1. Translate supplied task information into the context-bundle schema.
2. Load and persist explicit PStack Mode state within a declared scope.
3. Present one primary playbook without adding unstated goals or authority.
4. Supply a current capability catalog and resolve roles through the model-routing protocol.
5. Map routed seats into local model and agent interfaces.
6. Record the realized routing decision and every fallback.
7. Map worker and reviewer outcomes into the work-result schema.
8. Keep host-specific configuration outside this repository.
9. Preserve stop conditions and decision requests instead of converting them into automatic action.

An adapter must not use this core as an implied grant to access private data, invoke tools, change external state, or select an execution system. Those are all local policies of the consuming environment. A routing decision chooses a suitable seat; it does not authorize that seat to act.

## Human use

A person can use the repository without an adapter: write a short context bundle, choose a playbook, select capabilities from the routing policy, keep a decision trail, and produce a work result. Sticky mode requires a place to persist its state, but that place may be a checked-in or local JSON document rather than an agent host. The schemas are optional structure, not a runtime requirement.
