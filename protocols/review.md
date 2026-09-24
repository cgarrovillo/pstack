# Review protocol

Review tests a proposed result against its stated intent. It is not automatic approval and it does not mutate the result under review.

## Inputs

- Intent, scope, and acceptance criteria.
- The exact result or change set.
- Relevant surrounding context and known constraints.

## Procedure

1. State the intent in one clear paragraph before looking for flaws.
2. Review the result independently from at least two useful perspectives when risk justifies it: correctness, boundary safety, behavior, maintainability, evidence quality, or user impact.
3. Classify every finding as act on, consider, noted, or dismissed, with evidence and a short reason.
4. The owner decides whether to revise. Reviewers do not silently apply a change.
5. Re-check only the affected claims after revision and record residual risk.

## Result contract

Record: intent, perspectives used, findings by category, decision, evidence, and unresolved risks.
