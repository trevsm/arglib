# ArgML sketch

Illustrative DSL only. Not a committed grammar. These fragments are the language examples from the study.

## Claim

```argml
claim wage.employment.small_effect {
    proposition:
        effect(
            intervention = minimum_wage_increase,
            outcome = employment,
            population = low_wage_workers
        ) is small

    scope {
        jurisdiction = developed_market_economies
        horizon <= 3 years
        increase <= 20_percent
    }

    status = contested
}
```

## Scheme with critical questions

```argml
scheme expert_testimony<T> {

    premises {
        expert(E)
        expertise(E, domain D)
        asserts(E, proposition P)
        belongs_to(P, D)
    }

    supports P

    critical_questions {
        cq1: credible(E)?
        cq2: expertise_relevant(E, P)?
        cq3: consensus_among_experts(P)?
        cq4: evidence_supports(E, P)?
        cq5: conflicts_of_interest(E)?
    }
}
```

Instantiation:

```argml
use expert_testimony {
    E = economist_X
    D = labor_economics
    P = wage.employment.small_effect
}
```

## Inference families

### Deduction

```argml
deduction {
    premises = [P -> Q, P]
    conclusion = Q
    rule = modus_ponens
}
```

### Statistical induction

```argml
induction {
    population = voters
    sample = poll.sample_2026_08_15

    evidence {
        n = 2400
        estimate = 0.54
        sampling_method = ...
    }

    conclusion:
        support(candidate_A) ~= 0.54

    uncertainty:
        sampling_error = ...
}
```

### Abduction

```argml
abduction {
    observations = [O1, O2, O3]

    candidate_explanations = [H1, H2, H3]

    prefer H1 because {
        predictive_fit(H1) > alternatives
        complexity(H1) < H2
        prior_plausibility(H1) > H3
    }
}
```

### Causal

```argml
causal_argument {
    intervention = X
    outcome = Y

    model = causal_model.foo

    identification {
        estimand = ATE(X, Y)
        method = difference_in_differences
        assumptions = [
            parallel_trends,
            no_interference,
            stable_composition
        ]
    }
}
```

### Normative

```argml
normative_argument {
    factual_premises = [F1, F2]
    values = [
        value.welfare,
        value.autonomy
    ]

    principle =
        prefer(policy_A, policy_B)
        when welfare_gain(A, B) > threshold
        unless autonomy_cost(A, B) > threshold2

    conclusion = prefer(policy_A, policy_B)
}
```

## Objection

```argml
objection obj.external_validity {

    target = arg.minimum_wage.modest_employment_effect

    attack = undercut

    claim:
        historical_estimates_may_not_generalize(
            to = proposed_policy
        )

    reason:
        proposed_policy_outside_support_of_data
}
```

## Evaluation vector

```argml
evaluation arg.foo {
    deductive_validity = 1.00
    premise_support = 0.76
    evidence_quality = 0.81
    relevance = 0.95
    robustness = 0.64
    explanatory_power = 0.71
    assumption_sensitivity = 0.43
    novelty = 0.20

    epistemic_confidence = 0.69

    rhetorical {
        audience = policy_economists
        persuasiveness = 0.74
    }
}
```

## Epistemic context

```argml
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
```

## Abstraction candidate

```argml
scheme proxy_target_degradation {
    variables {
        G : underlying_goal
        M : proxy_metric
        A : optimizing_agent
    }

    premises {
        correlated(M, G)
        optimize(A, M)
        manipulable(M)
    }

    defeasible_conclusion:
        correlation_after_optimization(M, G)
        <
        correlation_before_optimization(M, G)
}
```

## Rhetorical rendering

```argml
rendering speech_17 {
    semantic_argument = arg.carbon_tax.112

    audience {
        knowledge = general
        priors = ...
        values = ...
    }

    rhetorical_strategy = [
        concrete_example,
        analogy,
        loss_framing
    ]
}
```

## Provenance

```argml
evidence e1034 {
    source {
        type = academic_article
        doi = "..."
        version = "v2"
        retrieved = 2026-08-19
    }

    locator {
        page = 17
        table = 4
        rows = [3, 4]
    }

    extraction {
        agent = model_X
        timestamp = ...
        confidence = 0.93
    }

    verification {
        human_review = true
    }

    supports = claim.c829
}
```

## Bayesian update

```argml
belief hypothesis.H {
    prior = 0.20
}

evidence E {
    likelihood {
        P(E | H) = 0.7
        P(E | not H) = 0.3
    }
}

update {
    posterior(H) = ...
}
```

## Decision model

```argml
decision_model {
    actions = [A, B, C]
    states = [S1, S2, S3]
    probabilities = ...
    utilities = ...
    constraints = ...
}
```

## Evaluation as argument

```argml
evaluation e12 {
    target = argument_A

    conclusion:
        relevance(argument_A) = low

    reason:
        premise_P concerns short_term effects
        while conclusion_C concerns long_term effects

    evaluator = critic_model_17
}
```
