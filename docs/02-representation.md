# Representation

The fundamental unit is an argument graph, not prose.

Natural language is a poor canonical storage format because it hides too much:

> Increasing the minimum wage will probably have only a small effect on employment because modern empirical studies find relatively small employment elasticities.

That sentence contains several separable things:

1. a policy intervention
2. a dependent variable
3. a quantitative empirical generalization
4. an appeal to a body of evidence
5. an inference from historical estimates to a contemplated intervention
6. implicit scope conditions
7. probably a claim about effect magnitude rather than sign
8. uncertainty

The canonical representation should expose those distinctions. Natural language remains the **surface syntax**, not the semantic core.

This follows the general direction already taken by the Argument Interchange Format, which separates informational nodes from nodes representing inferential or other argumentative relations. See [references](references.md).

## Three layers

### Layer 1: human language

Readable arguments, essays, debate transcripts, research papers.

### Layer 2: Argument Intermediate Representation (AIR)

A typed semantic graph.

### Layer 3: specialized executable models

Where appropriate:

- propositional or first-order logic
- Bayesian networks
- causal DAGs
- decision models
- utility models
- statistical models
- constraint systems
- legal rule systems
- temporal logic
- actual Lean / SMT proofs

The same argument can cross layers:

```text
Natural language
      ↓
AIR argument graph
      ↓
causal DAG + statistical evidence
      ↓
decision model
```

AIR functions somewhat like a compiler IR: sufficiently structured for tooling, but broad enough to represent heterogeneous reasoning.

## ArgML

A readable DSL that compiles to JSON/RDF. Identifiers matter: prose can change while the semantic object remains stable.

See [examples/argml-sketch.md](examples/argml-sketch.md) for the language sketches from the study.

## Object model

Minimum node types:

```text
Claim
Definition
Evidence
Argument
Warrant
Assumption
Value
Model
Objection
Rebuttal
Explanation
Context
Evaluation
Source
Agent
Version
```

Edges:

```text
supports
attacks
undercuts
rebuts
depends_on
instantiates
generalizes
specializes
equivalent_to
contradicts
defines
cites
assumes
uses_model
uses_value
addresses
supersedes
derived_from
```

An internal graph might look like:

```text
             E1 ─────┐
                     ▼
A1 ───────────────▶ P1
                     │
A2 ─────┐            │
        ▼            ▼
       P2 ───────▶ ARG-7 ─────▶ C
                    ▲  ▲
                    │  │
             warrant  assumption
                    │
          OBJ-3 ────┘
             │
             ▼
          REBUT-4
```

The graph itself is the intellectual object. A worked example with claims, arguments, objections, rebuttals, and competing policies is in [examples/congestion-pricing.md](examples/congestion-pricing.md).

## Graph integrity

### Contradiction detection

Easy:

```text
P
¬P
```

Hard:

```text
Economic mobility is high.
Economic mobility is low.
```

Those might differ in metric, population, time period, country, or absolute versus relative mobility. Contradiction checking therefore requires normalized claim semantics:

```text
measure
population
location
time
modality
quantifier
threshold
perspective
```

Only after unification should the system flag contradiction. Example of a machine-detectable pair:

```text
claim A:
  unemployment_rate(country=US, date=2026Q2, definition=U3) < 5%

claim B:
  unemployment_rate(country=US, date=2026Q2, definition=U3) > 7%
```

### Circular reasoning

Cycles are not automatically fallacious. Bayesian models, equilibrium arguments, coherence reasoning, and mutually reinforcing evidence can legitimately be cyclic.

The checker needs distinctions such as:

```text
foundational_dependency
corroborative_support
constraint_relation
equilibrium_relation
```

A circular proof error occurs when `A` ultimately depends on `A` through relations asserted as justificatory, and no independent support enters the strongly connected component. That can be detected graph-theoretically.

### Duplication and equivalence

At a million nodes, semantic duplication will dominate:

```text
Raising the price lowers demand.
Higher prices tend to reduce quantity demanded.
Demand usually falls when goods become more expensive.
```

These may all instantiate one generalized node. Canonicalization is needed at several levels:

```text
exact duplicate
paraphrase
logical equivalence
same argument scheme
subsumption
special case
stronger / weaker version
```

Compression agents should create hierarchies:

```text
generic argument
   ↓
domain specialization
   ↓
case-specific application
```

That parallels abstraction in mathematics and software.
