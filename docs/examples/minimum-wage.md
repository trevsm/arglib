# Example: minimum-wage employment effect

Surface sentence that hides too much:

> Increasing the minimum wage will probably have only a small effect on employment because modern empirical studies find relatively small employment elasticities.

The graph should expose intervention, outcome, empirical generalization, evidence body, external-validity inference, scope, magnitude-vs-sign, and uncertainty.

## Empirical claim

```argml
claim evidence.minimum_wage.elasticity {
    type = empirical_estimate

    proposition:
        employment_elasticity(minimum_wage) in [-0.20, 0.05]

    evidence {
        source = doi:...
        method = meta_analysis
        sample_size = ...
        publication_year = 2025
    }

    confidence {
        epistemic = 0.78
        calibration_class = empirical
    }
}
```

## Policy-facing claim

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

## Inference

```argml
argument arg.minimum_wage.modest_employment_effect {

    conclusion = wage.employment.small_effect

    premises {
        p1 = evidence.minimum_wage.elasticity
        p2 = claim.proposed_increase.within_observed_range
    }

    warrant {
        scheme = empirical_generalization
        rule =
            if intervention_effect_estimates_are_small
            and proposed_intervention_is_in_distribution
            then expected_effect_is_small
    }

    assumptions {
        no_major_regime_change
        measurement_is_comparable
        literature_not_severely_publication_biased
    }

    defeaters {
        objection.minimum_wage.monopsony_regime
        objection.minimum_wage.external_validity
        objection.minimum_wage.long_run_adjustment
    }
}
```

## Typed undercutter

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

This is already more useful than storing an essay: the warrant is explicit, the assumptions are named, and the defeaters distinguish “the conclusion is false” from “the evidence does not establish the conclusion.”
