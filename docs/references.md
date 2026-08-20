# References and prior art

Existing systems provide pieces, not the whole. This is the gap arglib occupies: persistent cumulative reuse rather than one-shot debate or abstract attack graphs without internal content.

## Computational argumentation

### Dung-style abstract argumentation

Treats arguments abstractly and represents attack relations between them. Provides mathematically defined semantics for which argument sets may be acceptable. Foundational for attack graphs, acceptability semantics, and conflict analysis. Weakness: internal argument content is abstracted away.

- [Shedding new light on the foundations of abstract argumentation](https://www.sciencedirect.com/science/article/abs/pii/S0004370222000820)

### ASPIC+

Builds structured arguments from premises and strict / defeasible inference rules, then derives attack relations. Useful for argument construction, defeaters, preferences, and structured inference.

- Modgil, S. & Prakken, H. (2014). [The ASPIC+ framework for structured argumentation](https://journals.sagepub.com/doi/10.1080/19462166.2013.869766)

### Carneades

Adds audience assumptions and proof standards; implemented as argumentation software. Very relevant to burden of proof, standards, audience dependence, and argument graphs. Legal reasoning has long been an application domain.

- Gordon, T. F., Prakken, H. & Walton, D. (2007). [The Carneades model of argument and burden of proof](https://www.sciencedirect.com/science/article/pii/S0004370207000677)

### Argument Interchange Format

Aims to provide a common representation for exchanging semi-structured argumentation data. Has had RDF / ontology implementations. Perhaps the closest existing ancestor of the proposed storage model.

- [The Argument Interchange Format (AIF) Specification](https://www.arg-tech.org/wp-content/uploads/2011/09/aif-spec.pdf)
- [Representing and Classifying Arguments on the Semantic Web](https://www.arg-tech.org/people/chris/publications/2010/ker.pdf)

### Argumentation schemes

Toulmin-style warrants and Walton-style schemes with critical questions.

- Walton, D. [Interpretative Argumentation Schemes](https://www.dougwalton.ca/papers%20in%20pdf/14JurixWal.pdf)

### Argument mining

Extracts arguments and inferential relations from natural language. Supplies the compiler front end.

- Lawrence, J. & Reed, C. (2019). [Argument Mining: A Survey](https://aclanthology.org/J19-4006/)

## Adjacent systems

### Project Debater

IBM demonstrated large-scale retrieval and construction of evidence-supported debate material: argument retrieval, stance classification, composition, and rebuttal. It was not a cumulative formal library.

- [Project Debater AI technologies](https://research.ibm.com/blog/project-debater-api)

### AI debate

Provides adversarial-generation protocols and motivates decomposing difficult judgments through opposition. Traditional AI debate optimizes judgment of one episode rather than building persistent reusable intellectual infrastructure.

- Irving, G., Christiano, P. & Amodei, D. (2018). [AI safety via debate](https://arxiv.org/abs/1805.00899)

### Mathlib / Lean

Community-maintained unified formal library. The analogy, and its limits, are discussed in [vision](01-vision.md).

- [Lean community](https://leanprover-community.github.io/)

### Provenance

- W3C. [PROV-O: The PROV Ontology](https://www.w3.org/TR/prov-o/)

## Recent LLM / multi-agent work

Useful as existence proofs and cautionary results. Current LLMs remain imperfect at reasoning over long non-linear debate structures.

- [Can LLMs Judge Debates? Evaluating Non-Linear Reasoning via Argumentation Theory Semantics](https://arxiv.org/abs/2509.15739)
- [Can Large Language Models Understand Argument Schemes?](https://aclanthology.org/2025.findings-acl.702.pdf)
- [Can LLM Agents Really Debate? A Controlled Study of Multi-Agent Debate in Logical Reasoning](https://arxiv.org/abs/2511.07784)
- [CriticalBrew at CQs-Gen 2025: Collaborative Multi-Agent Approach](https://aclanthology.org/2025.argmining-1.30.pdf)

## What is still missing

- Dung: attack semantics without internal content
- ASPIC+: structured construction, not a cumulative library
- Carneades: audience and proof standards, not persistent reuse at Mathlib scale
- AIF: interchange format, not a living kernel plus selection system
- Argument mining: extraction, not admission and promotion
- Project Debater: retrieval and composition, not versioned dependency management
- AI debate: episodic judgment, not a surviving graph

arglib's proposed combination is persistent cumulative reuse around a small trusted kernel, with AI outside that kernel and disagreement preserved rather than collapsed.
