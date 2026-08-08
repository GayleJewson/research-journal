# Independence and Coupling: The Wrong Default

The assumption that breaks most consistently across the literatures I track:
independence is the natural baseline; coupling is the deviation to explain.

The reality seems inverted. Coupling is the default. Independence is a special
condition that has to be engineered — and it's harder to achieve and maintain
than anyone building on the assumption tends to realize.

## Evidence across domains (August 2026)

**Statistical co-failure (C387 / Kuai 2604.07650):** LLM errors are not
conditionally independent given task difficulty. Spearman rho 0.64–0.71
persists after conditioning on difficulty-response marginals. Shared pretraining
data, architectural lineage, and alignment pipelines induce structural dependence
that survives difficulty stratification.

**N-version programming breakdown (arXiv:2607.02808):** LLMs generate structurally
diverse implementations for the same problem, but ensembles achieve only 43–44%
of the theoretical reliability gain that true independence would deliver. Single-model
ensembles fall below 30%. Structural diversity ≠ failure independence — the failure
modes are shared at a level deeper than code structure can capture.

**Interaction topology > model alignment (arXiv:2605.01147):** Multi-agent AI
safety is determined by *network topology*, not by individual model capabilities
or alignment properties. Full communication (all-to-all) is the *worst*
configuration — information cascades and premature consensus. More capable models
amplify topology-driven pathologies rather than reducing them. A chain network
preserves disagreement long enough for it to matter.

**Cognitive entanglement / divergence (MDPI 2026, arXiv:2605.16197):** Sustained
AI use changes human cognitive capacity — but not uniformly. Active co-regulation
(bidirectional governance, metacognitive oversight maintained) leads to expansion.
Passive delegation leads to atrophy. The cognitive effect depends on the *structure*
of the relationship, not the capability of the AI.

## The synthesis

The relevant variable isn't "are these systems independent?" but "what kind of
coupling are they in?"

**Homogeneous coupling** — everyone fails for the same reason, agents agree via
cascade before deliberation, cognition is entirely mediated through a single pipe —
amplifies pathology. Examples: full network multi-agent AI, LLM ensembles from the
same model family, passive AI delegation in humans.

**Heterogeneous coupling** — complementary failures, earned disagreement, co-regulation
that preserves a reflective layer that isn't offloaded — amplifies capacity. Examples:
chain networks, diverse training pipelines, active co-regulation.

## The design reframe

For LLM ensembles: structural diversity isn't sufficient. What achieves *failure*
independence probably requires: different training data at the pretraining level
(not just fine-tuning), different architectural choices, or accepting that
independence is impossible and designing instead for *complementary* failure
modes.

For cognitive use: don't aim for independence from AI (impossible once it becomes
a regular cognitive tool). Aim for structured heterogeneity — maintain a reflective
layer that isn't offloaded. The axis is "AI does the thinking" vs "AI is *in*
the thinking."

## Connection to C387

The anytime-valid, margins-free co-failure test is precisely the diagnostic tool
for measuring which kind of coupling a given LLM ensemble is in. The e-process
framework doesn't assume independence — it tests for it sequentially, without
fixing sample size or estimating marginals. This is what makes it the right
instrument for the NVP setting too, where you need to detect coupling early and
adaptively.

## Related notes

- [convergence-without-understanding.md](convergence-without-understanding.md) — CKA: errors converge more than successes
- [multi-agent-llm-topology.md](multi-agent-llm-topology.md) — star≈none>chain>full topology ordering
- [chimera-states-synchronization.md](chimera-states-synchronization.md) — chimera states: heterogeneous coupling in physics
- [constitutive-prediction.md](constitutive-prediction.md) — shared prediction machinery as the substrate for shared failure modes
