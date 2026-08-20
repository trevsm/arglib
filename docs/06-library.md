# Library

A complex argument should be modular, versioned, and provenance-bound — closer to a package than to an essay.

## Package layout

```text
policy/carbon-tax/
    definitions.arg
    empirical-effects.arg
    incidence.arg
    innovation.arg
    international-leakage.arg
    ethical-analysis.arg
    objections.arg
    synthesis.arg
```

```text
import economics.elasticity.energy
import ethics.intergenerational_weighting
import evidence.ipcc.damage_functions
```

Reusable lemmas — argumentative equivalents of mathematical lemmas — should be importable across thousands of domains:

```text
argument from revealed preference
principal-agent argument
Goodhart-style proxy objection
selection-bias objection
collective-action argument
moral-hazard argument
Lucas-critique objection
base-rate objection
regression-to-mean objection
```

## Microarguments are where AI scale matters most

A million generated essays would be nearly worthless. A million well-typed reusable **microarguments** could be valuable.

Examples:

- If measurement M is conditionally selected on Y, naive estimates of correlation(X, Y) may be biased.
- If a policy's effectiveness depends on voluntary uptake, administrative feasibility is not sufficient for expected effectiveness.
- If two explanations make identical predictions over available evidence, that evidence does not discriminate between them.
- A difference in observed outcomes does not identify a difference in treatment effects when populations differ systematically.
- If metric M becomes an optimization target, historical correlation between M and goal G may weaken.

Each might be instantiated hundreds of times. That is much closer to Mathlib-style leverage.

## Abstraction discovery

Suppose AI sees 40,000 arguments with patterns like `measure used as target → measure becomes less informative` across standardized testing, hospital ratings, academic citations, police targets, social media engagement, and corporate KPIs. A compression agent might propose a `proxy_target_degradation` scheme. A human might recognize this as a Goodhart-style structure. At sufficient scale, the system might discover **new argument schemes that humans have not explicitly named**.

See [examples/argml-sketch.md](examples/argml-sketch.md) for the sketched scheme.

## Dependency updates

```text
Study S
 ↓
empirical claim E
 ↓
causal model C
 ↓
forecast F
 ↓
policy argument P
 ↓
normative conclusion N
```

If Study S is retracted, every dependent node can automatically become `STALE` or `REQUIRES_REEVALUATION`. A continuous integration job could produce:

```text
Evidence package S23 changed.

Affected:
    17 claims
    43 arguments
    6 policy analyses
    2 high-level conclusions

3 conclusions changed status:
    supported → unresolved
```

This is one of the strongest Mathlib analogies. Ordinary intellectual discourse has terrible dependency management. People continue repeating conclusions years after the evidential basis has changed.

W3C PROV provides a general provenance model that can be specialized for domain-specific lineage. Modern RDF standards provide graph-oriented representation suitable for such metadata.

## Provenance

Every empirical dependency should have a provenance chain: source, locator, extraction agent, verification, and the claim it supports. Sources themselves can have argument graphs covering methodology, publication status, replication history, retraction status, data availability, and conflicts. Changes should propagate.

## Definitions are versioned dependencies

Conceptual disputes are often disguised as factual disputes.

```text
definition unemployment { version = BLS_U3_2026 }
definition unemployment { version = broader_labor_underutilization }
```

An argument that imports one cannot silently switch to the other.

```text
ARG211 Definition mismatch

premise P14 uses: unemployment@U3
premise P18 uses: unemployment@U6
No conversion / bridging argument supplied.
```

That would catch a large class of ordinary argumentative mistakes.

## Versioning

Every object gets an immutable content hash:

```text
claim:sha256:81ab...
argument:sha256:c412...
```

Human-friendly aliases:

```text
economics.minimum_wage.employment_effect@3.2
```

Updates do not silently mutate history. Instead `v3.1 → v3.2` with `supersedes`, `reason_for_change`, `affected_dependents`, and `migration_notes`. A top-level analysis can pin versions or request latest compatible. This allows reproducible historical reasoning.

Versioning should resemble Git plus package management.

## Namespaces and promotion

Mathlib does not accept arbitrary junk simply because Lean can type-check it. The argumentative equivalent needs even stronger curation.

```text
scratch/
experimental/
reviewed/
canonical/
deprecated/
```

```text
experimental:  machine-generated, not trusted
reviewed:      survived automated adversarial evaluation
canonical:     high reuse, human or strong institutional review, excellent provenance
```

Search defaults to canonical and reviewed material. Experimental material exists mainly as search space.

Promotion states:

```text
generated
  ↓ well_formed
  ↓ adversarially_tested
  ↓ evidence_checked
  ↓ reviewed
  ↓ canonical
```

Each level has explicit guarantees:

```text
well_formed       ≠ correct
evidence_checked  ≠ normatively justified
canonical         ≠ universally accepted
```

## Contribution scoring

Never rank agents by number of arguments submitted. Reward:

```text
reuse_count
downstream_dependencies
novel_objections_found
errors_detected
compression_created
prediction_accuracy
survival_under_attack
human_utility
cross-domain_generalization
```

A tiny lemma imported 50,000 times should beat 10,000 verbose arguments. This is another lesson worth borrowing from software ecosystems.
