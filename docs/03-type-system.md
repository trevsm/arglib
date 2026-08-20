# Type system

Trying to reduce all reasoning to generic `supports(A, B)` edges would lose too much. Claims, warrants, inference families, and defeaters each need first-class structure.

## Warrants are first-class

One of the most important design choices is separating `P because Q` into:

- premise `Q`
- conclusion `P`
- warrant `W` explaining why `Q` supports `P`

Otherwise most arguments contain hidden logic.

Toulmin-style warrants and the argumentation-scheme tradition are directly relevant. Walton and collaborators developed families of stereotyped argument schemes together with “critical questions” that identify characteristic ways those schemes can fail.

An argument instantiates a scheme. The checker cannot establish that an expert is trustworthy, but it **can** automatically instantiate the appropriate challenge set. That is highly valuable.

See [examples/argml-sketch.md](examples/argml-sketch.md) for `scheme expert_testimony<T>` and its instantiation.

## Inference families

Each family gets different verification rules:

```text
Deductive
Probabilistic
Statistical
Inductive
Abductive
Causal
Analogical
Defeasible
Conceptual
Normative
Practical
Strategic
Legal
Interpretive
Rhetorical
```

### Deduction

The system can completely verify modus ponens and similar rules.

### Statistical induction

Sample size, estimate, and sampling-error arithmetic can be checked. Representativeness cannot necessarily be.

### Abduction

There is no binary validity. The checker evaluates whether competing hypotheses were represented and whether scoring criteria were applied consistently.

### Causal reasoning

Hidden causal assumptions become explicit dependencies: estimand, identification method, parallel trends, no interference, stable composition.

### Normative argument

A normative conclusion requires at least one normative bridging premise. This prevents a common failure mode: presenting value-dependent conclusions as though they were empirical facts.

## Claim taxonomy

A claim could be typed as:

```text
empirical
logical
definitional
causal
predictive
counterfactual
normative
evaluative
interpretive
strategic
legal
conceptual
existential
universal
statistical
historical
testimonial
procedural
```

These types determine what counts as admissible support:

```text
empirical claim
    cannot be fully supported solely by normative premises

normative conclusion
    requires at least one normative bridging premise

causal claim
    requires a causal warrant, not merely correlation

universal claim
    vulnerable to counterexample

existential claim
    may be established by one authenticated instance
```

That is analogous to static typing preventing nonsensical programs.

An **argument type error** might be:

```text
ARG104:
Causal conclusion inferred from correlation
without causal identification rule.

  premise:
    ice_cream_sales correlates drowning

  conclusion:
    ice_cream_sales causes drowning

Possible missing dependencies:
    causal mechanism
    intervention evidence
    confounder control
```

This would not prove the conclusion false. It would show that the submitted argument does not establish it. That distinction is essential.

## Defeaters

Classical logic is monotonic: adding premises does not invalidate previous deductions. Ordinary reasoning is not.

```text
Bird(x) → normally Flies(x)
Bird(Tweety)
∴ Flies(Tweety)
```

until someone adds `Penguin(Tweety)`. This is why **defeasible reasoning** is central.

ASPIC+ distinguishes structured arguments and attack relations. Carneades models arguments together with burdens and different standards of proof.

ArgML should distinguish at least:

```text
rebuttal                 attacks conclusion
undercutter              attacks inference
premise_attack           attacks premise
exception                invokes exception to rule
alternative_explanation  competes abductively
scope_counterexample     shows overgeneralization
value_attack             rejects normative premise
definition_attack        disputes conceptualization
```

That distinction makes argument search dramatically better. The system knows whether somebody is saying “your conclusion is false” versus “your evidence does not establish your conclusion.” Those are different argumentative operations.

## Quality is a vector

A single “argument score” would quickly become misleading.

```text
Q(A) = (v, e, p, r, x, d, s, u, a, …)
```

Possible dimensions:

```text
deductive_validity
premise_support
evidence_quality
relevance
robustness
explanatory_power
assumption_sensitivity
novelty
epistemic_confidence
rhetorical.persuasiveness   # stored separately; see rhetoric rule
```

These dimensions should not all be combined unless a user supplies a weighting function. That allows queries such as:

```text
show strongest arguments for P
under:
    empirical_rigor > 0.8
    rhetorical_effect ignored
```

```text
show arguments most persuasive to:
    audience = skeptical_nonexpert
```

```text
show conclusions robust under both:
    utilitarian values
    rights-based values
```

This is where the system becomes much more than a debate database.

Admission score is also separate from argument strength. See [agents](07-agents.md).
