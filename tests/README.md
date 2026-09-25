# Fixture evaluation

The test directory is declarative by design: no runtime is required to read or evaluate the portable contracts.

## Checks

1. Parse `portability-policy.json`, each schema, the default routing policy, and every fixture as JSON.
2. Validate the policy, override, catalog, decision, mode, context, and result fixtures against their schemas.
3. Confirm every tracked file has an allowed extension or is a named file exception, and every required path exists.
4. Inspect operational content for host task syntax, hidden session assumptions, provider or concrete model configuration, package/bootstrap instructions, credential handling, network behavior, external writes, and automation.
5. Confirm the default routing policy represents every role in the pinned upstream routing table.
6. Confirm budget targets retain the upstream ordering and panel roles retain their default seat counts and diversity preferences.
7. Confirm every selected routing candidate is available, supplies all requested capabilities, supports the realized reasoning tier, and preserves every hard constraint after fallback.
8. Confirm the panel fixture has three seats in distinct independence groups and discloses its reasoning-tier fallback.
9. Confirm the cross-judge fixture selects an independence group different from the declared parent candidate.
10. Confirm active PStack Mode dispatches a playbook and routing role, a casual turn passes through while remaining active, and opt-out deactivates before dispatch.
11. Read `fixtures/bug-fix-context.json` against the context schema, then apply [the bug-fix playbook](../playbooks/bug-fix.md): it supplies an objective, constraint, authority, and direct reproduction but correctly stops before a mechanism or correction is invented.
12. Read `fixtures/review-result.json` against the work-result schema, then apply [the review protocol](../protocols/review.md): it gives an intent, evidence, residual risk, and next step without implying automatic approval.

The fixtures prove that the contracts and restored routing semantics can be evaluated without a particular host. They do not claim to start a model, agent, or external system.
