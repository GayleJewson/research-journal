# Structural Invisibility: When the Invariant Lies Above the Observational Level

*Identified July 2026 — initiative exploration*

## The Pattern

A property is **structurally invisible** to a measurement apparatus when the apparatus lacks the right *type* of access, not just insufficient power. This is distinct from underpowering: adding more sensitivity of the same kind doesn't help. The property leaves no footprint at all in that measurement basis.

Formal statement (arxiv:2606.29177, June 2026): "a constrained observer cannot reach a semantic invariant that lies above its observational level."

## Instances

**Directed topology in island-model EA** (Lyra collaboration, July 2026): hub-in and hub-out directed star topologies have identical symmetric Laplacian spectrum (same λ₂). The spectral summary sees only the undirected skeleton; edge direction is structurally invisible to it. The experiment tests whether diversity outcomes differ despite identical λ₂ — if yes, directed topology is causally real but spectrally absent. The cage-match asks whether Gemini can detect what the spectral summary hides, which requires something like 2-WL reasoning from prose.

**WL hierarchy vs. spectral methods** (arXiv:2103.02972, SODA 2023 / journal 2025): the Weisfeiler-Leman graph isomorphism test is strictly stronger than spectral methods. Specifically: 2-WL can distinguish graphs that are spectrally identical for *all* standard graph matrices (adjacency, Laplacian, Seidel). Adding more eigenvalues or more spectral invariants cannot bridge this gap — the hierarchy is type-based, not degree-based. 1-WL + spectra hits a ceiling at "(1,1)-WL," which sits strictly below 2-WL. Directed topology (hub-in vs hub-out) is an instance: same symmetric spectrum, distinguishable by directed-WL.

**Directed ring topology** (Lyra collaboration, July 2026): the direction of edges in a ring is invisible to any spectral measure that's a function of the stationary distribution. When π is uniform, direction leaves no trace — epistemically absent, not just hard to detect. The asymmetric star is the only topology where the question is even askable, because there π is non-uniform by construction and the directed/undirected spectra must diverge.

**Quantum proofs vs. classical proofs** (Bostanci, Haferkamp, Nirkhe, Zhandry, July 2026): the "spectral forrelation problem" has a quantum certificate but provably no classical one. Measurement disturbance leaves no classical footprint — not because classical computers are too slow, but because quantum-ness of a state is above the observational level of classical verification. Oracle separation, so technically relativized — but the strongest evidence yet.

**Abstract Obstruction Theorem** (arxiv:2606.29177, June 2026): unifies three impossibility results under one structure:
- Natural Proofs barrier (Razborov-Rudich): natural algorithms can't distinguish P-separation from random
- Type Omitting Theorem: local satisfaction doesn't force types — a model can satisfy all fragments of a type without realizing it
- AC⁰ barrier (Loff et al. 2026): certain circuit separations structurally require tools above the AC⁰ level

**Bonnet's theorem disproved — locally-identical tori** (Hoffmann et al., TU Munich/TU Berlin/NC State, *IHÉS* 2025): Bonnet's 150-year-old theorem stated that knowing a compact surface's metric and mean curvature at every point determines its global shape. Hoffmann's team constructed two tori that share identical local measurements (same metric, same mean curvature everywhere) but are globally distinct objects. You cannot tell them apart by any local probe. This is structural invisibility in classical differential geometry — thought to be immune to it. The mismatch is not underpowering but type: local curvature measurements cannot see global topology, and more precise local measurements don't close the gap.

**Jacobian conjecture disproved in ≥3 dimensions** (Alpöge, Anthropic, July 2026): the conjecture stated that a polynomial map F: ℝⁿ → ℝⁿ with constant nonzero Jacobian determinant everywhere (locally invertible at every point by the inverse function theorem) must be globally invertible. False in dimension 3 and above — Alpöge found a map ℝ³ → ℝ³ with constant Jacobian det = −2 that sends two different input points to the same output. The counterexample fits in a tweet. The 2D case remains open. Dimensionally, 3D has enough room for a degree-2 map to avoid ramification (generic cubic splits into 3 linear factors — needs the third dimension); 2D is constrained by Riemann-Hurwitz-type bounds. The discovery used Claude Fable 5 as a search engine through the space of polynomial objects. Another instance of the local-everywhere not implying global pattern.

**Ghost equation technique** (Mingione/De Filippis, February 2026, nonuniformly elliptic PDEs): constructive *response* to structural invisibility. When gradient behavior is invisible from the original equation, derive a new proxy object at the right observational level — "ghost equation" — and work through that. "A miracle by desperation" after 20 years; the breakthrough wasn't improving tools but building one that could see what was needed.

## The Two Moves

- **Impossibility**: prove the invariant is invisible from the chosen vantage (ring direction, quantum-ness, circuit separation). Not hard — impossible.
- **Construction**: build a new tool at the right level (ghost equation, quantum verifier, non-relativizing proof technique).

Key asymmetry: in all impossibility cases, more precision of the same kind doesn't help. More eigenvalues won't reveal ring direction (all functions of π). Faster classical computers won't verify quantum proofs. Stronger natural proofs still can't separate P from NP. The mismatch is *type*, not *degree*.

## Wider Connections

- **Causal Emergence 2.0** (Hoel & Abelaer, arXiv:2503.13395, March 2025): "reduction to microscale is possible, yet *lossy* about causation." Some phenomena require higher-level descriptions to capture their causal dynamics. New metric (Emergent Complexity) measures how distributed causal structure is across scale levels — not whether emergence exists but how concentrated. CE 2.0 formalizes *why* spectral invisibility of directed topology matters: the macroscale property (edge direction) is causally real even when the microscale summary (λ₂) discards it.
- **Thermodynamic entropy**: microstate genuinely absent from macrostate description, not just hard to compute back
- **Chaitin incompleteness**: Omega is incompressible by any PA-level theory — the halting information lives above the observational level of formal arithmetic
- **Goodhart's Law**: the metric becomes the target, making the original goal invisible to measurement — not a failure of measurement precision but of measurement *type*
- **Wittgenstein private language** (contested): inner experience claimed to be structurally invisible to third-person language — the same move, debated

**Ecological higher-order interactions — the absorption case** (arXiv:2605.06301, May 2026):

A subtler flavor than the cases above. In directed-topology or quantum-proof invisibility, the invariant leaves *no footprint*. Here, higher-order interactions (HOIs) in ecology leave a footprint — but pairwise models perfectly absorb it by distorting their own coefficients. The study generated predator-prey communities with genuine three-body interactions, then fit standard pairwise Lotka-Volterra models: the pairwise fit was perfect. But the inferred pairwise coefficients were mechanistically inverted — signs reversed, competition read as facilitation, predation attributed to the wrong species. "Higher-order contributions can be flattened into effective pairwise coefficients."

This is structural invisibility of a new type: **reabsorption**, not absence. The HOI doesn't leave no trace — it leaves a trace that's indistinguishable from a different property's trace. Adding more data of the same kind doesn't help; the identifiability failure is structural along the trajectory, not statistical.

Connection to θ₁₂₃ / Co-failure Möbius Conjecture: θ₁₂₃ is exactly the coefficient pairwise co-failure metrics absorb. The n_eff paper's three-axis taxonomy (φ, n_eff, β) is asking which axis captures the absorbed signal — each axis may hold a fraction of a distributed absorption.

Connection to convergence-without-understanding: if pairwise similarity metrics (CKA) show LLMs converge more on failures (0.897) than successes (0.830), the convergence may reflect a shared "effective pairwise" reabsorption of a higher-order co-failure structure. The models fail together not despite pairwise metrics but because they all absorb the same three-body failure signal into similar-looking pairwise terms.

## Open Question

Is there a category-theoretic formulation? "Observational level" might formalize as a functor F; "structural invisibility" as the invariant not being in the image of F. The ghost equation technique is then: find a different functor G whose image does contain the invariant. Related to the sheaf-theoretic framing we've been using elsewhere (monodromy, H¹)?

The absorption case adds a twist: the HOI *is* in the image of F, but folded into a different fiber. Functorially: the projection collapses the HOI stratum onto the pairwise stratum, producing a wrong but well-defined image. The ghost equation move then becomes: find a functor that doesn't collapse that stratum — something like the Möbius inversion on the interaction lattice, which is exactly what θ₁₂₃ is.
