# Target

Not Mathlib for truth. Not Wikipedia for arguments. Not an AI debate chatbot.

> **A version-controlled, typed, provenance-aware, adversarially maintained dependency graph of human reasoning.**

## What a result looks like

Instead of `THEOREM: P`, you might get:

```text
RESULT R441:

Given:
    A1, A7, A12
    empirical model M4
    evidence package E2026.08
    normative principles V2, V8

And provided:
    objection O19 is false

Then:
    policy P dominates policy Q
    under decision model D7

Robustness:
    survives 89% of tested parameter region

Open obligations:
    E91

Status:
    reviewed
```

That is genuinely machine-usable cumulative analytical knowledge.

## Mature architecture

```text
                    NATURAL LANGUAGE
                         │
                  Formalization Agents
                         │
                         ▼
                ┌──────────────────┐
                │ Argument IR / AIR│
                └────────┬─────────┘
                         │
        ┌────────────────┼─────────────────┐
        ▼                ▼                 ▼
 Logical engines   Probabilistic       Causal /
 SMT / Lean        reasoning           decision models
        │                │                 │
        └────────────────┼─────────────────┘
                         ▼
               Dependency / Attack Graph
                         │
          ┌──────────────┼──────────────┐
          ▼              ▼              ▼
      Evidence       Provenance      Definitions
      graph          graph           / ontology
          │              │              │
          └──────────────┼──────────────┘
                         ▼
                 Verification pipeline
                         │
              ┌──────────┼──────────┐
              ▼          ▼          ▼
           critics    synthesis   compression
              │          │          │
              └──────────┼──────────┘
                         ▼
                  Candidate library
                         │
                    selection
                         │
                         ▼
                  Canonical library
                         │
             ┌───────────┼────────────┐
             ▼           ▼            ▼
          Search      Analysis      Debate UI
```

## Routine operations

If the project works, these become ordinary:

```text
show me exactly what this conclusion depends on
show me which dependencies are factual vs normative
show me its strongest unresolved defeaters
show me the minimal disagreement between two positions
show me what breaks if this study is retracted
show me which arguments generalize to another domain
show me the strongest version of the opposing case
show me conclusions invariant across plausible assumptions
show me high-centrality uncertainties worth researching
show me reusable reasoning patterns nobody has abstracted yet
```

Those capabilities do not currently exist in anything close to Mathlib's cumulative form.

## Existing pieces, missing combination

The theoretical ingredients exist separately. Modern LLMs make automated formalization, generation, criticism, counterargument generation, and graph construction increasingly practical, though current research also shows that LLM judgment of complex non-linear argument structures remains imperfect.

The missing innovation is to combine those pieces around **persistent cumulative reuse** rather than one-shot debate.

If that worked, scale could matter considerably. AI would not merely generate more prose. It could perform large-scale search over candidate inferential structures, preserve successful intermediate abstractions, continually attack them, and propagate new evidence through their dependencies. That is sufficiently close to what formal mathematical libraries enable that the Mathlib comparison becomes technically substantive rather than metaphorical.

## Ceiling and middle ground

The ceiling is lower than mathematics because real-world reasoning never gets a universally trusted kernel for semantics, evidence, or values.

The achievable middle ground is still large:

- structural correctness can be formal
- empirical claims can be provenance-bound and continuously reevaluated
- probabilistic and causal submodels can be executable
- assumptions and values can be explicit
- disagreements can be localized
- arguments can be modular
- AI-generated contributions can compete for survival through adversarial evaluation and downstream reuse

The strongest version of the idea is impossible. The weaker version is not weak at all.
