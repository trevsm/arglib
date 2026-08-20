# arglib study

This directory is the project brief. It reorganizes a design study for a weaker, realistic analogue of “Mathlib for arguments.” Implementation is intentionally out of scope here.

Read in order if you are new to the project. Jump by topic if you are looking for a specific design choice.

## Reading order

1. [Vision](01-vision.md) — why the project is viable, and what it must not try to be
2. [Representation](02-representation.md) — argument graphs, AIR, ArgML
3. [Type system](03-type-system.md) — claims, warrants, inference families, defeaters, quality vectors
4. [Verification](04-verification.md) — obligation checking, compiler, trusted kernel
5. [Epistemology](05-epistemology.md) — contexts, disagreement localization, preserved pluralism
6. [Library](06-library.md) — packages, reusable lemmas, provenance, versioning
7. [Agents](07-agents.md) — argument search, adversarial debate, scale and selection
8. [Implementation](08-implementation.md) — first prototype and phased roadmap
9. [Risks](09-risks.md) — pseudo-formality, semantic canonicalization, Goodharting
10. [Target](10-target.md) — what “done” looks like
11. [References](references.md) — prior art

## Examples

- [ArgML sketch](examples/argml-sketch.md) — claims, schemes, inferences, objections
- [Minimum wage](examples/minimum-wage.md) — empirical claim plus inference
- [Congestion pricing](examples/congestion-pricing.md) — full worked graph

## Design invariants

These constraints should survive implementation choices:

1. The reusable product is a *conditional* result, not `C is true`.
2. Natural language is surface syntax. The semantic core is a typed graph.
3. Warrants are first-class. Hidden `P because Q` is a defect.
4. Different inference families have different verification rules.
5. Defeaters are typed operations, not generic disagreement.
6. Quality is a vector. Do not collapse it unless a user supplies weights.
7. Proof checking is obligation checking. Unresolved leaves stay visible.
8. The trusted kernel is small and deterministic. AI judgments live outside it.
9. Rhetoric is separated from epistemic support.
10. Disagreement is preserved, not resolved by an evaluator oracle.
11. Generation must be much cheaper than admission.
12. Never display a giant green `PROVED`.

## Original section map

The source study was numbered 1–78. That numbering is preserved here so later discussion can still cite it.

| Study §§ | Doc |
| --- | --- |
| intro, 1, 42–43, 77 | [01-vision.md](01-vision.md) |
| 2–3, 31–32 | [02-representation.md](02-representation.md) |
| 4–8 | [03-type-system.md](03-type-system.md) |
| 9–10, 33–35 | [04-verification.md](04-verification.md) |
| 11–12, 26–27 | [05-epistemology.md](05-epistemology.md) |
| 13–16, 21–22, 49 | [06-library.md](06-library.md) |
| 17–20, 28–30, 45–48, 66 | [07-agents.md](07-agents.md) |
| 53–65 | [08-implementation.md](08-implementation.md) |
| 44, 67–71 | [09-risks.md](09-risks.md) |
| 36–41, 50–52, 72–76, 78 | [10-target.md](10-target.md) plus [references.md](references.md) |
| 23–25 | [02-representation.md](02-representation.md) (graph integrity) |
