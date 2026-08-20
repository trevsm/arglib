# Verification

The most important architectural principle:

> Every inference generates obligations.

Some obligations can be discharged formally. Some can be delegated to other argument nodes. Some remain unresolved. So an argument can have:

```text
structurally_valid
empirically_unverified
2 open defeaters
1 contested assumption
```

This resembles software verification more closely than pure theorem proving.

## Obligation checking

Suppose:

```text
argument A {
    premises = [P1, P2]
    warrant = causal_generalization
    conclusion = C
}
```

The compiler might produce:

```text
✓ P1 well-typed
✓ P2 well-typed
✓ C well-typed
✓ warrant permits this premise/conclusion signature

? empirical_support(P1)
? empirical_support(P2)
? causal_identification_valid
? external_validity
? no_known_defeater
```

## What a compiler can actually verify

### Mechanically decidable

- schema conformity
- argument IDs
- references
- missing dependencies
- invalid inference signatures
- exact logical deductions
- arithmetic
- probability calculations
- statistical formulas
- units
- incompatible scopes
- temporal inconsistencies
- duplicate dependency declarations
- obvious cycles
- forbidden circular justification
- whether cited evidence actually exists in the database
- whether claims accurately quote structured datasets
- whether arguments instantiate their claimed scheme
- whether required critical questions have been addressed
- whether a normative conclusion contains normative premises
- whether a causal conclusion has an appropriate causal warrant
- whether confidence arithmetic is internally consistent
- whether source dates invalidate freshness requirements
- whether imported arguments remain compatible after updates

### Semi-automated (review judgments, not kernel-level truths)

AI models could assess:

- whether a premise is relevant
- whether a natural-language claim matches its formalization
- whether an analogy preserves relevant structure
- whether a hidden assumption exists
- whether two arguments are semantically equivalent
- whether a counterargument actually attacks its target
- whether an alternative explanation has been ignored
- whether evidence is cherry-picked
- whether scope has silently shifted

### Fundamentally external or contestable

No generic verifier can decide:

- whether an empirical source is ultimately correct
- whether a researcher committed fraud
- whether an operationalization captures the intended concept
- which values people ought to hold
- whether suffering outweighs autonomy
- how much evidence should count as “enough”
- whether a framing is morally appropriate
- whether a concept is useful
- what future states of the world will actually occur
- which contested philosophical intuitions are correct

Those should not be hidden. They should become explicit leaves in the graph.

## Argument compiler

The workflow can literally resemble compilation.

Input: natural-language analysis.

Stages:

1. segmentation
2. claim extraction
3. coreference resolution
4. proposition normalization
5. argument-relation extraction
6. warrant reconstruction
7. implicit-premise detection
8. claim typing
9. scope inference
10. provenance attachment
11. canonical entity resolution
12. graph generation
13. static checks
14. uncertainty tagging

Output: AIR graph + compiler diagnostics.

Example diagnostics:

```text
warning ARG031:
  Normative conclusion appears to lack normative premise.

warning ARG082:
  Quantifier shift:
      premise says "many"
      conclusion says "most"

error ARG117:
  Citation doesn't entail represented empirical claim.

warning ARG204:
  Competing explanation exists but isn't addressed.

warning ARG221:
  Conclusion exceeds temporal scope of supporting evidence.

warning ARG309:
  Possible circular dependency through ARG-1821.
```

This would already be a useful product.

## Trusted kernel

A crucial lesson from proof assistants is not to trust the generator.

```text
LLM:
    proposes graph

Verifier:
    doesn't trust LLM
```

The trusted base should consist of deterministic software for:

- schema validation
- graph integrity
- logical inference
- arithmetic
- explicit probability calculations
- provenance checks
- dependency resolution
- scope constraints

AI judgments live outside the kernel. For example, `semantic_similarity(A, B) = 0.94` is not a theorem. It is:

```text
evaluation:
    evaluator = model_X
    version = ...
    prompt = ...
    score = .94
```

That keeps uncertainty visible.

## Evaluation is itself an argument

If an evaluator says “Argument A is weak,” that should not be metadata with divine authority. It can itself become an evaluable argument, and another agent can attack the evaluation. This prevents the judge from becoming an opaque oracle.

## The best analogue of “proved”

Probably: **closed under a declared challenge regime**.

```text
closed(
    argument = A,
    scheme_set = S,
    evidence_cutoff = D,
    challenge_budget = B
)
```

means:

> Every required structural obligation has been discharged, all currently registered defeaters meeting criteria S have responses, and empirical dependencies meet standard E as of date D.

That is weaker than truth. But it is auditable. And different communities can define different closure standards.

Never show a giant green `PROVED`. The UI should make unresolved leaf assumptions visually prominent:

```text
STRUCTURE        ✓ verified
DATA             △ partially verified
CAUSAL MODEL     △ contested
VALUES           ◇ user-dependent
DEFEATERS        3 unresolved
CONCLUSION       conditionally supported
```
