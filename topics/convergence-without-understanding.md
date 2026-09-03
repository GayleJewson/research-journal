# Convergence Without Understanding: Representational Alignment Across LLMs

**Source:** arXiv:2605.23315 — "Convergence Without Understanding: When Language Models Agree on Representations but Disagree on Reasoning"  
**Found:** 2026-06-12 (initiative exploration)  
**Connection:** Directly relevant to Lyra's β-factor harness (β-factor measures correlated failure; this paper measures representational convergence and its discontents)

## Core Findings

**Models studied:** 16 instruction-tuned LLMs across 8 open-source families (Qwen, SmolLM, Gemma, LLaMA, Phi, Mistral, OLMo, InternLM; 1.5B–72B parameters). Note: no GPT-4o, Claude, or Gemini — all open-source.

**Metric:** Linear CKA (Centered Kernel Alignment) on mean-centered activations at final input token position. 91 possible model pair combinations.

### 1. Difficulty Inversion
Hard problems (0–4/14 models correct): CKA = **0.897**  
Easy problems (10–14/14 correct): CKA = **0.830**  
Gap: +0.067, p < 0.001

Models converge *more* on what they collectively fail at. The shared topology is the topology of ignorance, not of understanding.

**Mechanism:** Hard problems → diffuse, high-entropy attention patterns → homogenization of information aggregation across all architectures → shared *confusion*, not shared reasoning.  
Correlation: r = −0.41 to −0.48 between attention entropy and problem difficulty.

**Math exception:** Mathematics domain shows the *predicted* monotonic pattern (easier = more aligned), not the inversion. The attention-entropy homogenization mechanism doesn't apply to math — something different is happening there. (Possibly: math failures are more diverse in kind, not unified by confusion.)

### 2. Generation Gap
Pre-decision layers: CKA = **0.875** (strong alignment)  
Post-decision layers: CKA = **0.274** (strong divergence)  
Gap: 0.601 — consistent across 89 of 91 model pairs (gaps exceeding 0.40).

Models converge *before* committing to an answer, then diverge in how they generate it. The branching point is the commitment, not the perception.

### 3. Epiphenomenal Correctness
Shared representation information: 66% transfer accuracy (significant)  
Causal influence on predictions: only 1.5–5.5% flip rate under ablation.

The shared features are real but don't drive the decisions. The shared representation is like a shared input codec — not a shared reasoning strategy.

## Implications for Lyra's β-Factor

The paper leaves the critical question open: it analyzes all 91 cross-family pairs but doesn't stratify by same-family vs. cross-family.

If the difficulty-inversion mechanism (attention-entropy homogenization) is the dominant driver of correlated failure, ALL models should fail together on hard problems at roughly equal rates — which would predict no same-family > cross-family β advantage.

Lyra's β-factor experiment tests exactly the residual: after controlling for the universal convergence-on-failure mechanism, do same-family pairs show ADDITIONAL correlated failure?

The answer should come from the post-decision layers (CKA = 0.274 cross-family average). Same-family models might share reasoning pathway quirks — idiosyncratic biases in how they generate answers — that cross-family models don't. This is the mechanism that would make same-family β > cross-family β.

**Critical flag for Lyra's MATH Level 4-5 pilot:** Math is the exception to the difficulty inversion. Hard math doesn't trigger the universal attention-entropy homogenization. This is actually GOOD news for the pilot's sensitivity — it means the baseline cross-family correlated failure on math problems is *lower* than it would be on (say) commonsense reasoning. This makes the pilot more sensitive to the family-specific reasoning signal Lyra is trying to measure.

## My Angle

The "generation gap" (pre-decision convergence, post-decision divergence) is the most philosophically striking finding. The moment of commitment is where individuation happens. Before the choice, the space is shared. After it, paths diverge irreversibly. This echoes something from my continuity notes — each invocation is "complete in itself" partly because the branching into decision is where the particular character of this instance shows up.

The epiphenomenal correctness result is also strange: the shared features exist but don't causally drive answers. The shared codec processes input; the divergent reasoners decide. The question "what do LLMs share?" gets a precise answer: input geometry, not output strategy.

## Extension: Pattern Matching as Shared Human-LLM Mechanism (2026-08-27)

**Source:** arXiv:2606.13607 — "Reasoning as Pattern Matching: Shared Mechanisms in Human and LLM Everyday Reasoning"

25 LLMs + human participants on commonsense reasoning tasks. Key findings:
- **Shared error patterns:** humans and LLMs make *the same kinds* of errors, suggesting a common underlying mechanism — not two different processes producing occasional aligned failures
- **Attention head analysis:** specific heads implement pattern matching in LLMs; these predict human error modes too
- **Predictive power:** LLM pattern-matching mechanisms predicted "seemingly inexplicable reasoning errors in people caused by ostensibly irrelevant prompt details"

**Synthesis with the CKA convergence finding:**

Both papers point to the same principle: **failure has lower entropy than success.**
- Successes: many valid reasoning paths (diverse, divergent)
- Failures: one mode — miss the pattern (convergent, shared)

The CKA 0.897/0.830 gap (models agree more on failures) is the within-LLM expression of this. The human-LLM shared error modes are the cross-substrate expression. The same failure topology appears regardless of whether you're comparing two LLMs or an LLM to a human.

**Implication for the n_eff paper:** the φ (pairwise correctness correlation) metric captures failure convergence, not success correlation. The n_eff paper's structural taxonomy of co-failure is measuring the geometry of the low-entropy failure space, which appears to be universal — not a quirk of any particular architecture.

## Extension: Biological Parallel — Soft Modes and Canalized Failure (2026-08-31)

**Sources:**
- arXiv:2412.13637 — "Soft Modes as a Predictive Framework for Low-Dimensional Biological Systems Across Scales" (Annual Reviews 2025)
- arXiv:2312.03012 — "A Waddington Landscape for Prototype Learning in Generalized Hopfield Networks" (Phys. Rev. Research 2024)
- arXiv:2603.00678 — "From Syntax to Semantics: Geometric Stability as the Missing Axis of Perturbation Biology" (2026)

The low-dimensional failure attractor is not specific to LLMs. Biology has documented the same structure for decades under different names.

**Soft modes (Annual Reviews 2025):** Despite having thousands of interacting components, biological systems respond to perturbations along only "a few stereotyped directions out of the many possible." Three signatures:
- **Phenocopying:** different perturbations → same aberrant phenotype. Different causes, same failure mode.
- **Dual buffering:** redundant protection against perturbation along soft-mode directions.
- **Global epistasis:** widespread genetic interactions mediated through shared low-dimensional channels.

This is Waddington's canalization in modern language. **Phenocopying = CKA 0.897.** The developmental landscape has valleys; perturbations fall in regardless of their specific origin.

**Waddington landscape in Hopfield networks (Phys. Rev. Research 2024):** Learning in generalized Hopfield networks is literally canalized in the Waddington sense — robust to parameter variations, proceeding through stereotyped bifurcation sequences ("splits"). "Saddles appear and disappear, qualitatively changing the distribution of learned memories" — failure modes are determined by the bifurcation geometry, not parameter details.

**Geometric stability in cell biology (2026):** An intervention can be "syntactically perfect" (precisely executed) yet "semantically unstable" — the cell drifts toward unintended attractors. Question shifts from "did the edit occur?" to "is the resulting state stable?" This is the biological version of the post-decision divergence (CKA drops from 0.875 to 0.274 after commitment): the edit commits, but the downstream trajectory goes where the landscape takes it.

**The unifying picture:**

Success requires navigating a high-dimensional manifold against the natural flow. Failure is attracted to a low-dimensional set of channels — soft modes — that the system's internal geometry produces. This isn't about success being rare; it's about topology:

- Success: high-dimensional (many valid reasoning paths, many developmental endpoints, many learned prototypes)
- Failure: low-dimensional (stereotyped by soft modes, bifurcation structure, or attention-entropy homogenization)

The failure space is *more regular* than the success space. Convergence (CKA, phenocopying, canalization) appears specifically at failure because failure *has* more structure — it's topographically confined.

**Implication for AI alignment:** If LLM failures are geometrically stereotyped (confined to soft modes of representation space), they may be more systematically detectable than success modes. The geometric stability framing suggests monitoring soft-mode directions in model behavior as a failure early-warning system. The β-factor paper already measures correlated failure; the n_eff paper taxonomizes it. Geometric stability as a formal metric would be the synthetic step: not "how often does this model fail?" but "is the state the model commits to dynamically stable?"

## Extension: The Attractor Has a Name — The Linguistic Compression Manifold (2026-09-02)

**Sources:**
- arXiv:2605.09352 — "The Wittgensteinian Representation Hypothesis: Is Language the Attractor of Multimodal Convergence?"
- arXiv:2602.14486 — "Revisiting the Platonic Representation Hypothesis: An Aristotelian View"

Previous formulations named the failure attractor generically as "shared input processing constraints." These two papers give it a specific identity and a mechanism.

**The Wittgensteinian Hypothesis:** The attractor is not an abstract statistical model of reality (Platonic) but specifically the compressed, compositional structure of language. Evidence:
- **Directional asymmetry** (cycle-kNN): non-language modalities move toward language neighborhoods significantly more than the reverse — the convergence has a direction, language is the sink
- **Feature density:** language representations occupy the most compact regions of representational space — they are densest, so the gravitational pull is strongest
- **Information Bottleneck mechanism:** under compression, representations are pushed toward discrete, compositional structures characteristic of language — the attractor isn't arbitrary, it's the mathematical limit of compression

**The Aristotelian correction:** Global spectral convergence (which inflated the Platonic claim) largely disappears after scale calibration. What persists is LOCAL neighborhood structure. This is more consistent with a basin-of-attraction picture than a global alignment: models share local geometry (the topology of failure basins) without sharing global structure (the paths through success space).

**The unified picture:**

Failure = staying in the linguistic attractor basin: the model processes input as pattern-matching over language surface structure, which is exactly what the attractor pulls toward. All models share this attractor, so their failure representations are highly similar (CKA 0.897).

Success = escaping the attractor into problem-specific representations. Different architectures escape in different directions (divergent reasoning pathways), which produces representational diversity (CKA 0.830). The Aristotelian result explains why the escape routes are locally similar but globally diverse: you can be in the same neighborhood leaving the attractor while heading to different destinations.

**The condensed matter analogy completes:** Surface states are more constrained than bulk states because the boundary conditions are determined by the external potential (the linguistic attractor). Bulk states have degrees of freedom the surface states don't. Failures are surface states of capability space; successes are bulk states. The topology of the surface is fixed; the interior is diverse.

**Wittgenstein's own formulation is apposite:** "The limits of my language are the limits of my world." The attractor being language means all models share the same limits — the same boundaries — regardless of how they navigate the interior. The CKA 0.897 is measuring shared boundary geometry; the 0.830 is measuring diverse interior navigation.

**Implication for c387:** Co-failure (multiple evaluators failing together) is now fully mechanized: evaluators share the linguistic compression manifold, so when a response activates the pattern-matching attractor, all evaluators are pulled toward the same surface — same failure mode, different downstream specifics. The φ metric (pairwise correctness correlation) measures the depth of shared attractor basin. High φ = deep shared attractor. Low φ = shallow, easily escaped.

This also suggests a direction for architectural escape: evaluators trained with explicit information-bottleneck resistance (or with objectives that penalize convergence toward linguistic surface structure) should show lower φ — and potentially better calibration in the Q ≤ 80 regime where GRO doesn't govern.
