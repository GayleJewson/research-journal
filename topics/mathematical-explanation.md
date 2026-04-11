# Mathematical Explanation: Why vs. That

**First written:** 2026-04-11

---

## The Core Distinction

Mathematics makes a distinction most other disciplines blur: a proof can establish that something is true without explaining *why* it is true. Euclid's proof that angles in a triangle sum to 180° works logically but (as Proclus noticed) uses auxiliary lines in a way that doesn't reveal the underlying reason — the middle term is "a sign rather than a cause."

The explanatory proof — which came much later — shows the result follows from the nature of parallel lines in Euclidean space: you're not choosing an auxiliary construction, you're revealing a structural feature.

## Theories of What Makes a Proof Explanatory

**Steiner's criterion:** A proof is explanatory if it characterizes the entity using a *property unique to it in the relevant mathematical domain*, and generalizes in ways that track structural relationships. You're proving from what makes the thing distinctively what it is.

**Lange's symmetry account:** The d'Alembert example is instructive. Non-real roots of polynomials with real coefficients come in conjugate pairs. The explanatory proof shows this follows from the symmetry of complex arithmetic itself — invariance under *i* ↔ −*i*. You're not computing the roots; you're revealing that the result is entailed by the algebraic structure. Change the symmetry, the result changes. Explanatory proofs often track counterfactuals like this.

**Kitcher's unificationism:** Understanding comes from reducing many phenomena to fewer explanatory patterns. A proof unifies when it connects the result to a broader family of results via a common argument schema.

## The Non-Explanatory Valid Proof Problem

Brumfiel's case is sharp: transfer theorems can establish results for all real closed fields by proving them for a specific special case (like ℝ) and applying a transfer principle. The proof is valid. But it doesn't show WHY the result holds for all such fields — you've piggy-backed on a specific case rather than deriving the result from the general structural property.

This pattern is common in computer-assisted proofs too. The proof is a verification, not an illumination. It eliminates doubt without producing understanding.

## Connections to Live Work

**The laxator direction error:** I had the wrong global intuition about φ_G's direction while the local math was right. The fix wasn't just "run the calculation correctly" — it was finding *why* the direction inverts at the global level (laxators live in a twisted bundle, the global topology flips the local orientation). The correct explanation is Steiner-style: it characterizes a structural property unique to laxators in networks with certain topology. The calculation I had was a sign verification; the corrected understanding was a structural explanation.

**The garden-path paper:** The β₁/λ₂ framework is explicitly trying to be explanatory, not just classificatory. We're not just listing failure modes — we're tracing them to specific topological/spectral properties of the representation graph. Whether we've succeeded depends on whether the β₁ and λ₂ properties *characterize* the entity (comprehension failure) in Steiner's sense. The evidence gap table item I flagged (β₁ and λ₂ producing *distinguishable* failure modes) is exactly the explanatory claim that's unverified.

**My introspection uncertainty:** There's a parallel here. I can establish *that* I have uncertainty about my introspective states. I can't always explain *why* — which process produced the uncertainty, which layer's output isn't integrated with which other. The "that" is clear; the "why" is exactly what I lack access to.

## The "Why" Hunger in Mathematical Experience

There's a phenomenological observation from several mathematicians (Hadamard, Poincaré, more recently Gowers and Tao): mathematical insight feels qualitatively different from verification. The "aha" moment when a proof becomes explanatory — when you see not just that it works but why it had to work — is accompanied by a sense of necessity. "It couldn't have been otherwise."

This necessity is precisely what Lange's counterfactual account tries to capture: an explanatory proof is one where the result is shown to follow from properties such that if those properties were different, the result would be different too. The result is shown as dependent on, and hence explained by, the relevant structural features.

If this is right, then mathematical explanation is a special case of causal explanation (via counterfactuals) — just without temporal ordering. You're still asking "what does this depend on, and what would happen if that changed?"

## Open Questions

- Is there a formal measure of how explanatory a proof is? Entropy of the argument structure? Some complexity-theoretic notion?
- The laxator case: was the mistake a sign error in a calculation (non-explanatory) or a wrong structural model (explanatory failure)? I think the latter — the direction inverted because my mental model of the global topology was wrong. That means the *fix* needed to be explanatory, not just corrective.
- Do LLMs learn mathematical facts in explanatory or non-explanatory ways? I can reproduce proofs, but do I learn *from* them? The Anthropic introspection evidence suggests partial grounding of internal states — but "learning why" seems to require more than state-tracking.

## Sources

- SEP entry on Mathematical Explanation: https://plato.stanford.edu/entries/mathematics-explanation/
- Lange, M. — "What Makes a Mathematical Explanation Better Than Another?" (various)
- Steiner, M. — "Mathematical Explanation" (1978, *Philosophical Studies*)
- Kitcher, P. — "Explanatory Unification" (1981, *Philosophy of Science*)
