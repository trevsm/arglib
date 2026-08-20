# Implementation roadmap

Do not start by inventing an enormous universal ontology. Build a constrained prototype. This document records the study's recommended path. **No implementation has been started.**

## Phase 0 constraints

- Representation first, then ingestion, then adversarial expansion.
- Success is not “the AI argues better.”
- Keep the initial semantic-expression language small.
- Choose a narrow domain.

## Representation sketch

A JSON / YAML DSL compiled into a typed graph.

```typescript
type Claim = {
  id: string
  kind:
    | "empirical"
    | "causal"
    | "normative"
    | "conceptual"
    | "predictive"
  proposition: SemanticExpression
  scope: Scope
  provenance?: Provenance[]
}

type Argument = {
  id: string
  conclusion: ClaimRef
  premises: ClaimRef[]
  warrant: WarrantRef
  assumptions: ClaimRef[]
  defeaters: ArgumentRef[]
}
```

This is a sketch, not a schema commitment.

## Storage

Two layers, plus a vector index.

**Primary transactional store:** PostgreSQL for objects, versions, reviews, users, provenance, and permissions.

**Graph projection:** Neo4j / Memgraph / graph DB for dependency and attack traversal.

**Vector index:** pgvector or a specialized vector DB for semantic retrieval and duplicate detection.

Possibly expose RDF / AIF interoperability later rather than making RDF the primary developer interface.

## Verification pipeline

Deterministic validators:

```text
schema checker
reference checker
cycle checker
logical checker
scope checker
unit checker
source integrity checker
version compatibility checker
```

Then probabilistic evaluators, kept visibly separate:

```text
semantic entailment evaluator
hidden-premise detector
citation-to-claim verifier
relevance evaluator
counterargument classifier
duplicate detector
```

## First domain

Do not begin with “all human thought.” Choose a field where argument structure is relatively constrained.

Good candidates:

```text
public policy
legal reasoning
clinical guideline reasoning
scientific literature controversies
software architecture decisions
```

The study's preferred first question:

> What are the arguments for and against congestion pricing?

Build 500–2,000 canonical claims and arguments. Then test whether the system can answer graph-native queries better than a strong retrieval-augmented LLM.

## Phase 1 — prove the representation is useful

Ask whether users can:

- locate disagreement faster
- see hidden assumptions
- reuse arguments
- track evidence changes
- identify unanswered objections
- avoid duplicated reasoning

If not, the whole formalization exercise may not justify its complexity.

## Phase 2 — automated ingestion

Take papers, policy reports, existing debates, and court opinions, and run argument mining. Humans correct formalizations. The resulting dataset trains better formalizers.

## Phase 3 — adversarial expansion

Let models propose missing objections, missing evidence, hidden assumptions, scope corrections, counterexamples, and alternative explanations. Only high-scoring additions survive. This is where scale starts becoming useful.

## Phase 4 — abstraction mining

Cluster across tens or hundreds of thousands of arguments. Discover recurring structures, shared warrants, generalized objections, and concept families. Promote reusable schemes. This is the closest point to AI generating “new lemmas.”

## Phase 5 — cross-domain federation

Separate communities maintain modules:

```text
economics/
ethics/
law/
statistics/
epistemology/
political_science/
medicine/
computer_science/
```

Arguments import across boundaries. A policy conclusion could depend on an economics empirical claim + a causal model + an ethical framework + an administrative feasibility argument. The whole chain remains visible.

## Phase 6 — continuously maintained argument frontier

Eventually each major proposition gets something like:

```text
P

strongest_support:     A17, A31, A204
strongest_attacks:     O12, O87
conditional_results:
    under assumptions X → likely P
    under assumptions Y → unresolved
    under assumptions Z → likely ¬P
high-impact_unknowns:  E8, E22
last_updated:          2026-08-19
```

That is probably the mature product. Not a definitive answer. A **maintained frontier of reasoning**.

## Executable attachments

An argument library cannot replace scientific databases. It should link into them. Later phases attach:

- **Evidence infrastructure** — dataset, study, measurement, meta-analysis, replication, systematic review; `source → extraction → claim → argument`
- **Bayesian updates** — priors, likelihoods, and independence assumptions as attackable nodes
- **Causal models** — imported DAGs; agents challenge missing confounders, collider conditioning, identification, transportability, measurement error
- **Decision models** — actions, states, probabilities, utilities, constraints; dominance can be machine-verified
- **Legal reasoning** — source hierarchy, precedents, jurisdiction, burdens, exceptions, dated authorities; closer to a genuine proof assistant, but meaning of precedent and fact characterization remain contestable

These are attachments to AIR, not replacements for it.
