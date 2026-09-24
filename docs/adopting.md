# Adopting the portable core

Pstack is designed to be read directly or translated by another environment. The environment owns every operational decision: identity, permissions, context retrieval, execution, storage, review submission, and external writes.

## Safe adapter contract

An adapter should:

1. Translate supplied task information into the context-bundle schema.
2. Present a playbook without adding unstated goals or authority.
3. Map worker and reviewer outcomes into the work-result schema.
4. Keep host-specific configuration outside this repository.
5. Preserve stop conditions and decision requests instead of converting them into automatic action.

An adapter must not use this core as an implied grant to access private data, invoke tools, change external state, or select an execution system. Those are all local policies of the consuming environment.

## Human use

A person can use the repository without an adapter: write a short context bundle, choose a playbook, keep a decision trail, and produce a work result. The schemas are optional structure, not a runtime requirement.
