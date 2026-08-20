# Risks and hard problems

A formal-looking graph can create unjustified confidence. The architecture has to resist that.

## Pseudo-formality

Suppose:

```text
P1 = democracy is valuable
P2 = policy X increases democracy by 8%
C  = X should be adopted
```

The structure might be immaculate. But “what is democracy?”, “how was 8% estimated?”, “what are the costs?”, “compared with what?”, and “whose values?” could all be wrong.

A beautiful graph does not make its leaves true. The UI must make unresolved leaf assumptions visually prominent. Never show a giant green `PROVED`.

## Semantic canonicalization

This is the hardest unresolved problem, and it is not logic.

How do you determine whether “economic freedom” in argument A means the same thing as in argument B? How do you formalize “democracy is healthy” without injecting controversial interpretation? How do you know whether a model extracted the actual claim of a paper rather than a plausible nearby claim?

These are substantially harder than graph storage or inference checking. LLMs help, but current work still shows limitations in argument-scheme identification and reasoning over complex debate graphs.

Natural language cannot disappear. The structured representation must remain linked bidirectionally to source text.

## Goodharting the evaluation system

If agents optimize `argument score`, they will discover weaknesses in the scoring system:

- splitting arguments into artificial microclaims
- producing easy-to-defend trivialities
- avoiding ambitious claims
- maximizing citation count
- generating objections that look novel but aren't useful

Evaluation must be multi-objective and periodically adversarially audited. Human downstream usefulness should matter.

## Correlated AI error

Ten critic agents based on the same model family are not ten independent reviewers. They may all miss the same false assumption.

Deliberately introduce diversity:

- different model families
- different prompts
- different retrieval corpora
- specialized symbolic checkers
- human experts
- empirical tests

Recent controlled work on multi-agent debate similarly suggests that diversity and underlying reasoning capability matter more than merely adding debate structure.

## Adversarial rhetoric

A system capable of mining the most persuasive arguments for a particular audience can also optimize manipulation.

Rhetorical optimization should be isolated from epistemic ranking. The default public interface should probably rank evidential quality, robustness, and relevance — not maximum persuasion. Rhetorical experimentation requires additional governance.

## Combinatorial explosion of worldviews

Covered in [epistemology](05-epistemology.md). Evaluation must be lazy; you cannot materialize `2^n` assumption sets.

## Open-textured concepts

Formalizing “democracy,” “harm,” “fairness,” or “meaningful employment” can erase precisely what the dispute concerns. Definitions must be versioned dependencies, and conceptual mismatch must be a type error, not a silent rewrite. See [library](06-library.md).

## Garbage at scale

Scale causes `garbage generation ≫ human review capacity`. The architecture must optimize valuable surviving contributions per unit of human review cost. Generation must be much cheaper than admission. See [agents](07-agents.md).
