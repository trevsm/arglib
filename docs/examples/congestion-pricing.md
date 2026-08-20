# Example: congestion pricing

A computable debate, not a collection of paragraphs.

## Normative conclusion

```argml
claim congestion_pricing.should_adopt {
    type = normative
    proposition:
        ought(city, implement(congestion_pricing))
}
```

## Primary case

```argml
argument cp.primary_case {

    conclusion = congestion_pricing.should_adopt

    premises {
        p1 = congestion_pricing.reduces_congestion
        p2 = congestion_pricing.reduces_pollution
        p3 = congestion_pricing.revenue_can_improve_transit
        p4 = congestion_pricing.distributional_harm_is_mitigable
    }

    values {
        v1 = value.reduce_travel_time
        v2 = value.reduce_pollution
        v3 = value.distributive_fairness
    }

    warrant {
        scheme = practical_reasoning
        text =
          "Prefer policies whose expected benefits outweigh
           costs subject to fairness constraints."
    }

    confidence = 0.76

    dependencies {
        import transport.congestion.externality
        import economics.road_pricing
        import ethics.distributive_compensation
    }
}
```

## Empirical subargument

```argml
argument congestion_pricing.reduces_congestion {

    conclusion:
        congestion_after_pricing
        <
        congestion_without_pricing

    evidence {
        london.study.2019
        stockholm.study.2021
        singapore.study.2024
    }

    warrant = cross_city_empirical_generalization

    assumptions {
        city_has_viable_transit_substitutes
        charge_is_large_enough_to_change_behavior
    }

    confidence {
        epistemic = 0.86
    }
}
```

## Objection (premise attack)

```argml
objection cp.regressive {

    target = cp.primary_case
    attack = premise_attack

    conclusion:
        congestion_pricing imposes
        disproportionate burden
        on low_income_commuters

    support = [
        distribution.study.X,
        claim.low_income.schedule_rigidity
    ]

    confidence = 0.69
}
```

## Rebuttal

```argml
rebuttal cp.rebate {

    target = cp.regressive

    premises {
        congestion_revenue > rebate_cost
        targeted_rebates_feasible
    }

    conclusion:
        regressivity_can_be_substantially_mitigated

    assumptions {
        political_system_implements_rebate
    }
}
```

## Competing policy

```argml
competing_policy expanded_transit {
    intended_goal = reduce_congestion

    compare_to congestion_pricing {
        effectiveness = ...
        cost = ...
        equity = ...
        feasibility = ...
    }
}
```

This is the study's preferred first prototype domain: arguments for and against congestion pricing, 500–2,000 canonical claims and arguments, then a comparison of graph-native queries against a strong retrieval-augmented LLM. See [implementation](../08-implementation.md).
