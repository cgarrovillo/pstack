# Maintenance

## Versioning

Version the portable contracts independently. A change is breaking when it changes a required field, a stop condition, or the meaning of a result status.

## Reviewing changes

For every change:

1. Name the affected protocol or playbook and intended behavior.
2. Update a fixture when the contract changes.
3. Check the portability policy and file boundary.
4. Re-read provenance if material upstream-derived wording changes.

## Upstream imports

Follow [UPSTREAM.md](../UPSTREAM.md). Treat an upstream update as a reviewable proposal, not a synchronization event. The portable core may reject an idea that conflicts with this repository's boundary.
