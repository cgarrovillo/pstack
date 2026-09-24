# Decision trail protocol

Use a small durable trail whenever a task spans multiple decisions, people, or verifiable units.

## Minimum record

| Field | Meaning |
| --- | --- |
| Decision | What was chosen or deferred. |
| Alternatives | Material options considered. |
| Evidence | References and observations that support the choice. |
| Constraints | Scope, authority, cost, or compatibility limits. |
| Confidence | High, medium, or low, with a reason. |
| Follow-up | The next check, owner, or trigger for reconsideration. |

Keep the trail concise and update it when evidence changes the decision. A decision trail should make a later continuation cheaper without becoming a verbatim activity log.
