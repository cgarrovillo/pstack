# Fixture evaluation

The test directory is declarative by design: no runtime is required to read or evaluate the portable contracts.

## Checks

1. Parse portability-policy.json, each schema, and every fixture as JSON.
2. Confirm every tracked file has an allowed extension or is a named file exception, and every required path exists.
3. Inspect the portable content for host-specific task syntax, hidden session assumptions, provider configuration, package/bootstrap instructions, credential handling, network behavior, external writes, and automation.
4. Read fixtures/bug-fix-context.json against the context schema, then apply [the bug-fix playbook](../playbooks/bug-fix.md): it supplies an objective, constraint, authority, and direct reproduction but correctly stops before a mechanism or correction is invented.
5. Read fixtures/review-result.json against the work-result schema, then apply [the review protocol](../protocols/review.md): it gives an intent, evidence, residual risk, and next step without implying automatic approval.

Those two fixtures are intentionally small. They prove the contracts can be understood without a host environment; they do not claim to execute a system.
