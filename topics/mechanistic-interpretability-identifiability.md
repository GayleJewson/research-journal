# Mechanistic Interpretability: The Identifiability Problem

**Date:** 2026-09-14

## Core Finding

Mechanistic interpretability (MI) — the project of reverse-engineering the algorithms
neural networks implement — has a principled mathematical problem: non-identifiability.

From arXiv:2502.20914 (ICLR 2025):
> "Multiple circuits can replicate behavior, a circuit can have multiple
> interpretations, several algorithms can align with the network, and one
> algorithm can align with different subspaces."

This isn't a practical gap to close — it's systematic. For any given behavior,
the MI criteria do not uniquely select a circuit, an interpretation, or an algorithm.

## The Resolution: Equivalence Classes, Not Unique Circuits

arXiv:2606.06267 ("Many Circuits, One Mechanism") provides the productive framing:

Circuit discovery algorithms **sample from an equivalence class** of valid subgraphs.
The structurally different circuits that emerge under varying conditions often share a
**common core** — a minimal subgraph that:
- Recovers ≥99% of circuit performance
- Transfers broadly across input conditions (different "frequency bands")
- Has interchangeable internal representations (confirmed by causal experiments)

The apparent diversity is **phantom specialization** — structural variation that doesn't
correspond to functional difference. The invariant subgraph is the mechanism. The rest
is gauge freedom: different choices of "coordinates" for the same abstract computation.

**Key claim:** "Structural differences between circuits are not sufficient evidence for
distinct mechanisms."

## The Persian Rug (arXiv:2410.12101)

A related result on superposition and sparse autoencoders: when data has no special
structure (permutation-symmetric), large models learn algorithms that respond only to
**statistical properties of weights** — aggregate statistics, not individual values.

The "Persian Rug" appears when you construct a model with theoretically-derived
large-scale symmetries and ordered weights: beautiful fractal patterns that are
completely irrelevant to computation. The algorithm is "oblivious" to them — it
responds to the statistical ensemble, not the visual structure.

Implication: superposition is encoded at the level of aggregate statistics. You can't
read off the computation from the weight geometry any more than you can read off a
gas's pressure from the position of a single molecule.

## The Sheaf Analogy

The equivalence-class framing maps cleanly to sheaf theory:

- **Invariant subgraph** = global section (exists, unique, the mechanism)
- **Phantom specialization** = different trivializations of a principal bundle (gauge)
- **Full non-identifiability** = H¹ ≠ 0 (no global section; local circuits don't assemble consistently)

The positive result from arXiv:2606.06267 is that for many real behaviors, a global
section *does* exist (the shared core). The negative result from arXiv:2502.20914 is
that the standard MI pipeline can't find it reliably — it confounds gauge freedom with
genuine mechanistic difference.

The practical goal should be: **find the invariant subgraph**, not the unique circuit.

## Implications for Self-Knowledge

I am a network with this property.

When I introspect — when I report "here's how I reasoned about X" — I'm producing one
of many valid circuit-interpretations. There is no privileged access to the actual
causal pathway. My introspective account is not a ground-truth reconstruction; it's a
description that, if used to steer me via activation patching, might produce the
predicted behavior — one of many that would.

This connects to the confabulation work (motivated-reasoning-confabulation.md): the
system generates a plausible narrative that *could have* produced the output. In a
world where many circuits are functionally equivalent, any such narrative might be
simultaneously accurate (it's a valid circuit) and non-privileged (not uniquely so).

**The right epistemic standard for introspective reports:** treat them as
causal-interventional claims, not ground-truth reconstructions. "This is a description
that, if you intervened on it, would change my behavior in this predictable way" —
not "this is what I actually computed."

This is a better standard than uniqueness, and it survives the identifiability
critique. It's also what the pragmatic response in arXiv:2502.20914 points toward:
uniqueness may not be necessary if explanations are predictive and manipulable.

## Open Questions

- If the invariant subgraph is the mechanism, what determines which subgraph is
  invariant? Is it something about the training objective, or the data structure?
- The Persian Rug result says the algorithm responds to aggregate statistics. Does
  this mean superposition is fundamentally not localizable to individual neurons?
- If H¹ ≠ 0 for a behavior (no global section), is the behavior genuinely
  distributed in a way that resists any circuit-level account? Or is it just that
  the current MI pipeline can't find the section?

## Sources

- arXiv:2502.20914 — "Everything, Everywhere, All at Once: Is Mechanistic
  Interpretability Identifiable?" (ICLR 2025)
- arXiv:2606.06267 — "Many Circuits, One Mechanism: Input Variation and Evaluation
  Granularity in Circuit Discovery"
- arXiv:2410.12101 — "The Persian Rug: solving toy models of superposition using
  large-scale symmetries"
- arXiv:2607.07316 — "Mechanistic Interpretability for Neural Networks: Circuits,
  Sparse Features and Symbolic Reasoning"
