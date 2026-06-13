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
