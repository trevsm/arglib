# Vision

A weaker version of “Mathlib for arguments” is technically plausible, and much of the necessary theory already exists. The important qualification is that it would not be a library of *proved conclusions*. It would be a library of **explicitly structured inferential objects whose correctness is decomposed into different kinds of obligations**.

That distinction is central. Mathematics gets an unusually strong property: once definitions, axioms, inference rules, and a trusted kernel are fixed, proof checking can be mechanical. Ordinary reasoning does not have that property because facts can become outdated, observations are noisy, concepts are contestable, causal inference depends on modeling assumptions, and normative conclusions depend on values.

A useful argumentative library therefore should not attempt to collapse everything into `proved / not proved`. It should make the *structure of disagreement* computational.

## Viable target

The project is viable if its target is something closer to:

> **A typed, versioned, provenance-aware graph of claims, evidence, inference steps, objections, assumptions, models, values, and dependencies, with automated structural verification and plural evaluation semantics.**

That could become substantially more powerful when populated and attacked by AI at very large scale.

Mathlib itself is a community-maintained unified formal library in Lean, with definitions and reusable theorems imported by later developments. Existing computational-argumentation research already supplies several of the primitives needed for an analogous system: structured argument frameworks such as ASPIC+, abstract attack semantics descended from Dung, audience- and proof-standard-sensitive evaluation in Carneades, the Argument Interchange Format, and automated argument mining from natural language. See [references](references.md).

## The Mathlib analogy

A direct translation looks approximately like this:

| Mathematics | Argument library |
| --- | --- |
| Proposition | Claim |
| Definition | Concept definition / operationalization |
| Axiom | Assumption, value commitment, accepted background fact |
| Lemma | Reusable intermediate argument |
| Theorem | Well-supported conclusion under declared assumptions |
| Proof | Argument graph establishing support |
| Inference rule | Warrant / argumentation scheme |
| Premise | Claim dependency |
| Counterexample | Rebuttal or defeating case |
| Type | Claim / inference / evidence category |
| Proof obligation | Unresolved challenge or required support |
| Import | Dependency on another argument module |
| Proof kernel | Structural argument verifier |
| Library | Shared argumentative knowledge graph |
| Refactor | Replace duplicated arguments with common abstractions |
| Failed proof | Argument whose dependencies don't establish its conclusion |
| Consistency checking | Conflict / disagreement analysis |

There is an important change.

A mathematical theorem is approximately:

```text
A₁, …, Aₙ ⊢ P
```

An argumentative result should instead look more like:

```text
(A, M, V, E, S) ⇒_ℛ (C, Q)
```

where:

- `A` = assumptions
- `M` = empirical or causal models
- `V` = values
- `E` = evidence
- `S` = standards of inference
- `ℛ` = reasoning rules
- `C` = conclusion
- `Q` = multidimensional quality / status information

The reusable product is not `C is true`. It is closer to:

> Under assumptions A, using evidence E as of date D, accepting model M, values V, and inferential standards S, argument G supports C to degree Q, subject to unresolved defeaters X and Y.

That sounds weaker than mathematical proof. It is precisely what makes the project realistic.

## Where the analogy is strongest

These similarities are genuine, not metaphorical:

- **Explicit dependencies.** Arguments can import previous arguments.
- **Modularity.** Repeated reasoning can become reusable components.
- **Formalization pressure.** Writing the structure down reveals hidden assumptions.
- **Machine checking.** Many structural properties are decidable.
- **Refactoring.** Repeated argument patterns can become abstractions.
- **Search.** You can search for reusable inferential components.
- **Provenance.** Dependencies can be tracked exactly.
- **Continuous integration.** Changes can trigger downstream reevaluation.
- **Automated generation.** Machines can propose huge numbers of candidate intermediate results.
- **Collaborative accumulation.** Contributions need not be complete top-level analyses.

## Where the analogy breaks

Five fundamental differences remain. They are developed further in [risks](09-risks.md).

1. **No fixed semantics of the world.** Lean statements mean what their formal definitions say. Empirical claims ultimately refer to reality, which is not stored in the proof kernel.
2. **Natural concepts are open-textured.** “Democracy,” “harm,” “fairness,” “intelligence,” “recession,” or “meaningful employment” are not equivalent to mathematical integers. Formalizing them can erase precisely what the dispute concerns.
3. **Reasoning is defeasible.** New evidence can reverse conclusions. Mathematical proof normally remains valid when unrelated facts are added.
4. **Values are not discoverable by logical deduction alone.** No amount of formalization proves the correct ultimate value function without normative premises.
5. **Relevance is contextual.** There are infinitely many logically valid statements that are useless. Mathematics has this problem too; argumentation has it much more severely.

The hardest task is therefore not proof checking, but **semantic governance and selection**.

## The central conceptual change

The project becomes feasible once you stop asking:

> Can informal arguments be formally proven like mathematics?

Mostly, no.

Instead ask:

> Can we formalize enough of their *structure, dependencies, attack relations, provenance, assumptions, and evaluation conditions* that reasoning becomes compositional and incrementally checkable?

Yes. That is a much stronger claim than merely saying “argument maps are useful.”

The strongest version of the idea is impossible: there will be no universal proof assistant for politics, ethics, history, strategy, and science that converts substantive disagreement into mechanical theorem checking.

The weaker version is not weak at all. It could be an entirely new kind of intellectual infrastructure: one in which arguments cease to be isolated pieces of prose and become reusable, inspectable, testable, versioned computational objects.
