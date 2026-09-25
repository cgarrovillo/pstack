# pstack

PStack is a portable core of engineering practices for turning an explicit objective and evidence into a small, reviewable result. It includes declarative playbooks, a sticky task dispatcher, and capability-based model routing. It is documentation, schemas, policies, and fixtures only. It does not install itself, start a process, reach the network, access credentials, select a provider, or make an external change.

## Start here

1. Activate or load [PStack Mode](protocols/pstack-mode.md) for the declared scope.
2. Assemble an explicit [context bundle](schemas/context-bundle.schema.json).
3. Let PStack Mode select a task shape in [the selection guide](playbooks/selection.md).
4. Resolve the required roles through the [model-routing protocol](protocols/model-routing.md).
5. Apply the relevant [principles](principles/README.md) and protocols.
6. Record the outcome with the [work-result schema](schemas/work-result.schema.json).

Every procedure describes inputs, evidence, authority, stop conditions, and a result contract. A consuming environment may adapt those contracts to its own interfaces, but it must supply all context and enforce authority itself.

## Contents

| Area | Purpose |
| --- | --- |
| [principles/](principles/) | Small rules for scope, architecture, verification, collaboration, and learning. |
| [playbooks/](playbooks/) | Task shapes for fixes, features, refactors, investigations, performance work, prototypes, and continuation. |
| [protocols/](protocols/) | PStack Mode, model routing, context, parallel work, review, quality, and decision-trail contracts. |
| [routing/](routing/) | Provider-neutral default role, budget, panel, diversity, and fallback policy. |
| [schemas/](schemas/) | Portable JSON schemas for context, mode state, routing, and results. |
| [docs/](docs/) | Adoption and maintenance guidance. |
| [tests/](tests/) | Declarative portability policy and readable fixture evaluations. |

## Portability boundary

The default branch is deliberately not a plugin, runtime, agent profile, or automation product. Routing rules name roles and capabilities, never a provider or concrete model. Mode state is explicit, never hidden host state. The repository contains no executable source, package manifest, host configuration, integration credential, or external write path. An adapter belongs outside this repository and may not change the meaning of a core protocol.

## Provenance and license

This project is an independently maintained, deliberately rewritten extraction of reusable ideas from an upstream source. See [UPSTREAM.md](UPSTREAM.md) and [NOTICE](NOTICE). The retained license is [MIT](LICENSE).
