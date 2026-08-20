# Agents, search, and scale

A serious implementation should not have one model “reason deeply.” It should turn reasoning into a persistent adversarial process over a surviving graph.

## Argument search resembles proof search

Query: would national adoption of policy X probably improve welfare?

An argumentative search engine could recursively decompose it:

```text
Does X achieve intended outcome Y?
 ├─ causal mechanism?
 ├─ empirical evidence?
 ├─ external validity?
 ├─ implementation constraints?
 └─ behavioral adaptation?

What are secondary effects?
 ├─ cost
 ├─ distribution
 ├─ substitution
 ├─ strategic response
 └─ long-run equilibrium

Does Y imply welfare improvement?
 ├─ normative weights
 ├─ affected populations
 ├─ opportunity costs
 └─ rights constraints
```

Agents then expand open obligations. This begins to resemble theorem search. The objective is not `find proof(P)`. It is:

```text
construct Pareto-efficient argumentative frontier around P
```

where the frontier contains strong cases for P, against P, conditional on A, conditional on ¬A, and alternative explanation E.

## Debate as adversarial search

```text
Proposer:             construct strongest support graph for P
Attacker:             find minimal defeater
Repairer:             repair argument while preserving conclusion
Counterexample agent: search for violating instances
Alternative agent:    construct competing explanation
Assumption hunter:    expose unstated premises
Evidence agent:       verify leaf claims
Judge ensemble:       evaluate unresolved semantic issues
```

Cycle:

```text
generate → attack → repair → attack again → compress → generalize
```

AI-debate research has investigated adversarial interaction as a way to expose information that would otherwise be difficult for a human evaluator to assess. The persistent graph is more important than the debate transcript. A debate transcript is ephemeral. An argument graph survives.

## Debate should not have a winner

Traditional debate encourages optimizing persuasiveness. A knowledge system should optimize something closer to:

```text
information gain + error discovery + robustness improvement
```

Agents should get credit for destroying their own side's arguments.

```text
critic reward:
+4 novel valid defeater
+3 previously hidden assumption
+2 scope correction
+1 redundancy discovery

-3 irrelevant objection
-4 duplicate objection
-8 fabricated evidence
```

A successful debate might end with:

```text
Original proposition: P

Result:
    P is too broad.

Refined conclusions:
    P1 strongly supported under C1
    P2 unresolved under C2
    P3 probably false under C3

New distinction discovered: D
Critical empirical uncertainty: E
```

That is far more useful than declaring Team A victorious.

## Rhetoric is separated from epistemic support

Persuasion is not the same thing as justification. The graph should distinguish `epistemic argument` from `rhetorical realization`. The same underlying argument could have several renderings — technical paper, policy memo, five-minute debate speech, explanation for a teenager — with independent rhetorical metrics.

Persuasion experiments can then be conducted **without corrupting the epistemic graph**. That separation is essential if the system is supposed to improve reasoning rather than merely produce more effective propaganda.

## Graph-aware retrieval

Vector search alone is not enough. Queries should include:

- Find arguments supporting P.
- Find undercutters of argument A.
- Find arguments depending on assumption X.
- Find conclusions invalidated if study S is removed.
- Find strongest objections not answered by argument A.
- Find arguments structurally analogous to A in another domain.
- Find the minimal assumption differences separating P and ¬P.
- Find unresolved leaf claims with highest downstream influence.
- Find claims with high centrality and low evidential confidence.

Those queries are impossible to do reliably over ordinary prose collections. They become natural over the graph.

Centrality can prioritize research:

```text
research_value(x) ≈ uncertainty(x) × downstream_influence(x) × decision_importance(x)
```

Human reviewers should focus on bottlenecks: high-centrality new abstractions, contested semantic equivalences, important empirical source conflicts, novel arguments surviving many attacks, and normative disputes affecting many conclusions.

## Evolutionary search, strong selection

The scale hypothesis is plausible only with staged selection. You do not merge 10⁸ objects.

1. **Syntactic filter** — reject malformed objects
2. **Semantic deduplication** — remove paraphrases and trivial variants
3. **Adversarial challenge** — try to break each candidate
4. **Usefulness** — does it solve any open obligation?
5. **Generality** — can it be reused elsewhere?
6. **Novelty** — does an equivalent argument already exist?
7. **Empirical verification** — for evidence-dependent contributions
8. **Promotion** — only a tiny fraction enter the canonical library

```text
generate variation → select → retain → reuse
```

The crucial asymmetry:

> **Generation must be much cheaper than admission.**

Otherwise the library becomes a landfill.

Suppose:

```text
1,000,000 generated
  100,000 syntactically valid
   10,000 nonduplicate
    1,000 survive critics
      100 genuinely useful
       10 broadly reusable
        1 major conceptual abstraction
```

That could be an excellent outcome. The system should be designed like a search engine over intellectual possibility, not like Wikipedia where every submitted paragraph is expected to be worth preserving.

Scale has both a positive and a negative phase transition. At small scale, AI-generated arguments are mostly a productivity feature. At very large scale the system can begin searching **argument space**. But scale also causes `garbage generation ≫ human review capacity`. AI only helps if automated rejection scales at least as well as automated generation.

Optimize:

```text
valuable surviving contributions / human review cost
```

not the number of generated arguments.

## Novelty and synthesis

A novelty agent could classify a candidate as duplicate, minor variation, new application, new synthesis, new objection, new abstraction, or potentially new scheme. A strong new contribution may not be a new conclusion. It may be: these apparently unrelated debates have the same underlying structure.

Synthesis is a first-class operation. If position A explains observations 1, 2, 3 and position B explains 3, 4, 5, a synthesis agent searches for model C that explains 1–5 while retaining the best dependencies from both. Record `derived_from`, `resolves`, and `introduces assumption` rather than presenting synthesis as untraceable prose.

## Scoring

Separate **admission score** from **argument strength**.

```text
S_admit = wₙN + wᵣR + wᵍG + wᵤU − w_dD − w_cC
```

where N = novelty, R = robustness, G = generality, U = expected reuse, D = duplication, C = verification cost.

Argument epistemic quality gets a separate vector: logical, empirical, causal, scope, uncertainty, defeater resistance.

Rhetorical scores remain entirely separate. Otherwise persuasive but unreliable arguments can dominate.

## Worker set

A production system could use approximately:

```text
Formalizer
Generator
Critic
CounterexampleSearcher
EvidenceRetriever
EvidenceVerifier
AssumptionHunter
ScopeChecker
CausalCritic
NormativeCritic
Analogist
Compressor
AbstractionMiner
Synthesizer
NoveltyEvaluator
GraphMaintainer
HumanReviewRouter
```

Each agent emits typed proposals rather than directly mutating canonical state.

## Debate protocol for candidates

1. Generator proposes.
2. Three independent critics attack.
3. Generator or repair agent addresses attacks.
4. Critics attack the repaired version.
5. Evidence verifier checks leaf claims.
6. Compression agent compares with the library.
7. Evaluator estimates novelty / generalizability.
8. Promotion decision.

Persist the best objections even if the original argument is rejected. A failed argument can still add knowledge.
