# Epistemology

Argument status should be parameterized by an epistemic context. This may be the single most powerful feature.

## Contexts

Different audiences accept different models, values, priors, and proof standards. Evaluation is always `evaluate P under Γ`, never a context-free “who wins.”

```text
context alice {
    accepts = [
        climate_model_set_2026,
        utilitarian_value_framework
    ]
    rejects = [
        strong_precautionary_principle
    ]
    proof_standard.empirical = strong
    prior.P = 0.3
}

context bob {
    accepts = [
        climate_model_set_2026,
        rights_based_framework
    ]
    proof_standard.empirical = moderate
    prior.P = 0.6
}
```

Query:

```text
evaluate policy.carbon_tax under alice
evaluate policy.carbon_tax under bob
```

Possible answer:

```text
Alice:
    supported, confidence 0.81

Bob:
    unresolved, confidence 0.48

Minimal disagreement set:
    value.distributive_tradeoff
    assumption.elasticity_long_run
```

This is far more informative than saying Alice and Bob “disagree.” It identifies the **minimal cut set of assumptions responsible for the disagreement**. That becomes an important analogue of theorem-prover diagnostics.

## Disagreement localization

A mature system should not merely answer “which side wins?” It should answer:

> What exactly must differ between two internally coherent positions for them to reach different conclusions?

Suppose two argument graphs agree on 93% of their dependencies. The system could find:

```text
Conclusion divergence depends on:

1. probability estimate:
   P(severe_damage | warming=3C)
   Alice: .42
   Bob: .18

2. discount rate:
   Alice: 1.5%
   Bob: 4%

3. value premise:
   weight(future_person) = 1
   vs 0.7
```

That transforms debate. Instead of repeatedly debating the top-level proposition, participants can investigate the actual disputed nodes.

## Preserve disagreement

A large failure mode would be letting an evaluator LLM quietly decide contested questions.

```text
claim moral.status.animals {
    status = disputed

    positions {
        P1 { proposition = equal_consideration;      support = [...] }
        P2 { proposition = discounted_consideration; support = [...] }
    }
}
```

Arguments depending on either branch remain computable. The library does not need one official worldview. It can maintain many coherent worlds.

## Conditional knowledge

A user could ask:

> Assume animal suffering counts equally to human suffering and that cultured meat reaches cost parity by 2032. What follows?

The system traverses only compatible branches. This is analogous to theorem proving under assumptions `Γ ⊢ P`, except `Γ` might contain facts, priors, values, models, definitions, and proof standards.

```text
Γ_user ⊨_argumentation P
```

This is one of the strongest parts of the Mathlib analogy.

## Combinatorial explosion

If you have 100 assumptions, there are `2^100` possible assumption sets. You cannot precompute every worldview.

Evaluation must be lazy. Only instantiate contexts requested by users or discovered as decision-relevant. Use symbolic techniques:

- assumption dependency sets
- minimal sufficient conditions
- minimal inconsistent sets
- decision diagrams
- SAT / SMT solving

to compress worldview space.

## Competing foundations

Mathlib largely shares foundations. Argument reasoning will not. You might have packages like:

```text
ethics/utilitarian
ethics/deontological
economics/neoclassical
economics/institutionalist
epistemology/bayesian
legal/originalist
legal/purposivist
```

Arguments explicitly import foundations. Then you can ask:

> What conclusions are invariant across these frameworks?

Those invariant conclusions are especially interesting. They are analogous to robustness results.

## Robustness may replace proof

For messy reasoning, perhaps the strongest result is not “P is proven.” It is:

> P survives a large set of plausible assumptions, models, values, and attacks.

```text
R(P) = Pr_{Γ ~ 𝒞}(P supported under Γ)
```

where `𝒞` is a class of reasonable contexts. Then compare propositions by:

```text
assumption robustness
model robustness
evidential robustness
value robustness
adversarial robustness
```

This may be a better epistemic concept for real-world analysis than pretending we can have theorem-like certainty.
