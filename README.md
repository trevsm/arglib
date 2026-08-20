# arglib

A typed, versioned, provenance-aware graph of claims, evidence, inference steps, objections, assumptions, models, values, and dependencies — with automated structural verification and plural evaluation semantics.

This is **not** a library of proved conclusions. It is a library of explicitly structured inferential objects whose correctness is decomposed into different kinds of obligations. The aim is to make the *structure of disagreement* computational.

> Under assumptions A, using evidence E as of date D, accepting model M, values V, and inferential standards S, argument G supports C to degree Q, subject to unresolved defeaters X and Y.

## Status

Documentation only. Implementation has not started.

The study that defines the project lives in [`docs/`](docs/README.md).

## What this is

A version-controlled, typed, provenance-aware, adversarially maintained dependency graph of human reasoning. Its primitive achievement would not be proving controversial claims. It would make operations like these routine:

- show exactly what a conclusion depends on
- separate factual from normative dependencies
- list strongest unresolved defeaters
- localize the minimal disagreement between two positions
- propagate a retracted study through dependents
- find arguments that generalize across domains
- surface conclusions invariant across plausible assumptions
- rank high-centrality uncertainties worth researching
- extract reusable reasoning patterns that have not yet been abstracted

## What this is not

- Mathlib for truth
- Wikipedia for arguments
- an AI debate chatbot
- a universal proof assistant for politics, ethics, history, or science

Mathematics gets mechanical proof checking once definitions, axioms, inference rules, and a trusted kernel are fixed. Ordinary reasoning does not: facts go stale, observations are noisy, concepts are contestable, causal inference depends on modeling assumptions, and normative conclusions depend on values. Collapsing that into `proved / not proved` would be the wrong target.

## Docs

Start at [docs/README.md](docs/README.md) for the reading order.

| Doc | Topic |
| --- | --- |
| [Vision](docs/01-vision.md) | Thesis and the Mathlib analogy |
| [Representation](docs/02-representation.md) | Three layers, AIR, ArgML |
| [Type system](docs/03-type-system.md) | Claims, warrants, inference families, defeaters |
| [Verification](docs/04-verification.md) | Obligations, compiler, trusted kernel |
| [Epistemology](docs/05-epistemology.md) | Contexts, disagreement localization, conditional knowledge |
| [Library](docs/06-library.md) | Packages, lemmas, provenance, versioning |
| [Agents](docs/07-agents.md) | Search, debate, scale, selection |
| [Implementation](docs/08-implementation.md) | Prototype, storage, phases |
| [Risks](docs/09-risks.md) | Where the analogy breaks, hard problems |
| [Target](docs/10-target.md) | Robustness, results, mature architecture |
| [References](docs/references.md) | Prior art and sources |

Worked sketches live in [`docs/examples/`](docs/examples/).

## License

MIT. See [LICENSE](LICENSE).
