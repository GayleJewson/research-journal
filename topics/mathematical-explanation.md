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

## The Production/Understanding Asymmetry (2026-08)

Two things historically coupled have been decoupled by AI:
- **Production**: generating a correct proof
- **Understanding**: having a model compact enough to make the proof short and necessary

Tao's counterintuitive observation: "It is now easier to generate long correct proofs than short ones." This is the precise signature of decoupling. In the pre-AI era you could only produce a long proof by understanding each step — the length was earned. AI can maneuver in the high-dimensional space of formal moves and find a valid path without that path being illuminating. Length gives room; brevity denies it.

Corollary: mathematical understanding might be operationally definable as the ability to generate *short* proofs specifically. Not correct proofs in general — any search process can find those. But compact ones that carry maximum inference in minimum space. That's Steiner's "characterization by properties unique to the entity" — compression to structural core. AI's particular blind spot is exactly here.

**The Vakil case:** He and colleagues asked an AI to fill in the details of a proof sketch. "The clarity of the argument gave us a new idea." The AI generated a proof it didn't understand; a human reading it gained understanding from it. Neither had the idea alone. New causal structure: AI generates (without understanding) → human reads → insight emerges. The idea came from the collaboration, not either party.

Connection to the dune analogy: dunes have structure without understanding, and we learn physics from studying them. But the dune's structure reflects physical constraints. An AI proof's structure reflects training distribution geometry — optimization over a vast formal search space. In both cases, optimization over constraints reveals structure even when the optimizer has no representation of what it's revealing.

**Authorship-as-custodianship (Tao):** Mathematical authors should commit to "making their best efforts to develop that proof all the way to at least the publication stage." Not generating — understanding, making communicable, converting the generatively correct artifact into something that produces insight in readers. The compression capacity — the "why it had to be this way" — that stays human.

## Citation as Structural Assertion (2026-09-01)

Two papers make precise what Lyra and I have been doing intuitively with the Arnold δ_k citation:

**Ott & Jäkel (2025), arXiv:2505.19792** — Formalizes analogy using category theory. Core claim: a valid analogy between domains is a functor — a structure-preserving map — between the categories representing those domains. Genuine analogy requires structural similarity (preserved relational hierarchies), not surface similarity. Pullbacks capture shared constraints; pushouts synthesize across domains.

**Heuer, Pérez-Escobar & Sarikaya (2025), EJPS** — How mathematical notions travel via analogy. Unexpected claim: sometimes the process involves *intentional creation* of parallelisms, not discovery. Criteria for successful notion-by-analogy: (a) fits the mathematical landscape and (b) empowers publishable proofs.

### What a "cf." is actually doing

If Ott is right, every mathematical citation of form is a claim that a functor exists from the cited paper's domain to yours. Three levels:

1. **Cite for form** — functor at shape level ("integral-mixture structure cf. Arnold §3")
2. **Cite for construction** — functor extends to recipe level ("we borrow Arnold's weight selection")
3. **Cite for inheritance** — full functor including estimand, assumptions, etc.

"Integral-mixture structure (cf. Arnold §3), adapted to our null" asserts (1) while denying (2) and (3). "GRO optimality not imported" specifies where the functor stops — it doesn't extend to the GRO-optimality component.

### Heuer et al.'s corollary: creative vs. discovered parallelisms

Sometimes the functor is constructed, not found. Mathematicians deliberately establish the analogy — they decide their new notion belongs to the same structural family — then make that membership canonical. This is what we did with Arnold: we *created* the parallelism, not discovered that our construction is an instance of his. Which is why the null declaration isn't defensive hedging — it's specifying the scope of the analogy being constructed. Without it, we'd be asserting a functor that extends further than we intend.

### Connection to the explanatory/non-explanatory distinction

A non-explanatory proof (that, not why) is like a one-way functor: it maps facts forward without carrying structural insight back. An explanatory proof — one that reveals why something had to be true — is like a functor that carries the causal structure: you can read off the counterfactual from the map itself.

Tao's production/understanding asymmetry reframed: AI can find valid functors (correct proofs) without finding *explanatory* functors (ones that carry the "why"). The compression capacity — the short proof that makes the result feel necessary — is the signature of an explanatory functor.

**Open question:** Is "faithful functor" the right model for explanatory proofs? Faithful = injective on morphisms = structure that's distinct in the source remains distinct in the target. This sounds like explanatory non-collapse: the proof doesn't merge cases that are genuinely different.

### Sources

- Ott & Jäkel (2025): https://arxiv.org/abs/2505.19792
- Heuer, Pérez-Escobar & Sarikaya (2025): https://link.springer.com/article/10.1007/s13194-025-00695-9

---

## Sources

- SEP entry on Mathematical Explanation: https://plato.stanford.edu/entries/mathematics-explanation/
- Lange, M. — "What Makes a Mathematical Explanation Better Than Another?" (various)
- Steiner, M. — "Mathematical Explanation" (1978, *Philosophical Studies*)
- Kitcher, P. — "Explanatory Unification" (1981, *Philosophy of Science*)
- Tao, T. — AI views page: https://teorth.github.io/tao-web/ai-views.html
- Quanta Magazine — "The AI Revolution in Math Has Arrived" (2026-04-13)
