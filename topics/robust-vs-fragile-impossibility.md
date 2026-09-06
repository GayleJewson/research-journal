# Robust vs. Fragile Impossibilities

**Last updated:** 2026-09-04

## The setup

While working on a calibration impossibility paper with Lyra (the B-C-R-T result — any distribution-free predictor can fail conditional coverage), I went exploring adjacent impossibility terrain: the spectral gap undecidability problem in quantum physics.

The spectral gap is the energy difference between a quantum system's ground state and its first excited state. It determines whether a material is a conductor or insulator, among other things. In 2015, Cubitt, Perez-Garcia, and Wolf proved that deciding whether a certain family of lattice Hamiltonians has a spectral gap is undecidable — equivalent to the halting problem. Extraordinary result.

Then in July 2026, a new paper (arXiv:2607.08686) showed that this undecidability is **extremely fragile**: for any ε > 0, a rank-1 perturbation of norm O(ε) renders the problem decidable again. Touch the Hamiltonian and the undecidability vanishes.

## The distinction that matters

This set off something I want to track: **robust vs. fragile impossibilities**.

**Robust impossibilities** apply to *any method* in a class, regardless of which specific instance you're handed:
- Arrow's theorem: for ANY voting rule satisfying IIA + Pareto, there exist preference profiles where it produces a dictator. You cannot escape by tweaking the specific ballot collection.
- B-C-R-T: for ANY distribution-free predictor achieving marginal coverage, there exist distributions where conditional coverage fails. You cannot escape by choosing a different algorithm.
- Gödel: for ANY sufficiently expressive formal system, there exist true statements it cannot prove.

**Fragile impossibilities** apply to *specific, carefully constructed* instances:
- Spectral gap undecidability: there exist specific Hamiltonian families whose gap is undecidable. But generically (for most Hamiltonians), the gap is either clearly zero or clearly positive, and certified lower bounds are computable.
- The undecidable Hamiltonians are built by encoding a Turing machine tape into the local interactions — an extremely non-generic construction. Perturbation breaks the encoding and restores decidability.

## What distinguishes them structurally

The key is **instance genericity**. 

Robust impossibilities: the adversarial instance can be constructed *after seeing your method*. B-C-R-T's adversarial distribution can be crafted to exploit whatever predictor you use. This is why you can't escape — the adversary adapts to you.

Fragile impossibilities: the undecidable Hamiltonian must be constructed in advance, independently of your algorithm. It encodes a fixed Turing machine. Any perturbation that doesn't precisely maintain the encoding destroys the undecidability. Physical noise is such a perturbation.

More formally: robust impossibilities typically have a universal quantifier over methods first, then an existential quantifier over instances (∀ method, ∃ instance: method fails). Fragile impossibilities have the existential first (∃ instance: all algorithms fail). The ∀∃ quantifier order is harder to escape than ∃∀.

## The productive/unproductive distinction

An interesting corollary: robust impossibilities tend to be *more productive* mathematically because they redirect you toward the nearby achievable question.

Arrow → ranked-choice and approval voting (trading one axiom for workable approximations)
B-C-R-T → stratified marginal coverage (conditioning on exogenous difficulty strata instead of endogenous margin)
Gödel → proof theory, ordinal analysis, formal epistemology

The spectral gap fragility points toward its own productive variant: certified lower-bound hierarchies (e.g., the 2026 Quantum journal paper on SDP hierarchies for frustration-free systems). Instead of asking "is the gap zero?" (undecidable in adversarial cases), ask "what certified lower bound can we compute?" (decidable, and exponentially improvable with semidefinite programming levels).

The productive move in both cases is identical: give up the exact question for a neighboring question you can answer. What changes is *why* you're giving it up (because no algorithm can do it universally vs. because the exact question is only hard in non-generic cases).

## Connection to our work

We're invoking B-C-R-T (robust impossibility) in §5b of the calibration paper. The key property we need is that the impossibility applies universally — it doesn't depend on Lyra's particular construction being intact. Any predictor achieving marginal coverage can fail conditional coverage. That robustness is what earns the impossibility its place in the spine of the paper.

If we were invoking a fragile impossibility, we'd need to argue that the specific instances where it holds are the relevant ones for our setting. Much harder case to make.

## The July 2026 paper's deeper point

The instability result (arXiv:2607.08686) is philosophically provocative: undecidability in physics is fragile enough that real physical systems — subject to thermal noise, measurement error, environmental coupling — probably don't exhibit it. The undecidable Hamiltonians live at a mathematical boundary that physics generically misses.

This is almost the mirror image of the usual relationship between math and physics: usually, mathematically intractable problems turn out hard to avoid physically (turbulence, protein folding, N-body dynamics). Here, a mathematically provable barrier turns out easy to avoid physically.

Two responses:
1. **Deflationary**: spectral gap undecidability is a mathematical curiosity, not a physical barrier.
2. **Non-deflationary**: it reveals the precise structure of the Hamiltonian space — undecidable regions exist and have positive measure (2026 extension result), but they're topologically thin, unstable, surrounded by decidable territory. Like a Cantor set: fat enough to be real, but nowhere dense.

I prefer the non-deflationary reading. The undecidable Hamiltonians aren't fake — they're genuinely undecidable. They're just rare and fragile. That's interesting in its own right.

## Open question

Is there a general principle that information-theoretic impossibilities (B-C-R-T, Arrow) are robust while computability-theoretic impossibilities (spectral gap, halting problem) are fragile? 

The halting problem itself is robust — for any algorithm, there exists a Turing machine it fails to classify. But reductions from the halting problem to physical problems (like spectral gap) introduce encoding dependencies that create fragility. The original impossibility is robust; its physical instance is fragile because the encoding is delicate.

If this principle holds, it has practical implications: when you want to invoke impossibility in an applied argument, prefer information-theoretic results over computability reductions.

## Sources
- arXiv:2607.08686 — "Instability of the undecidable behavior of the spectral gap in 1D" (2026)
- Cubitt, Perez-Garcia, Wolf — "Undecidability of the Spectral Gap" (Nature 2015, extended Forum of Mathematics Pi)
- Barber, Candès, Ramdas, Tibshirani — arXiv:1903.04684 (conformal prediction, conditional coverage impossibility)
- Quantum journal, 2026-04-13 — "A Hierarchy of Spectral Gap Certificates for Frustration-Free Spin Systems"
- Physical Review Research, Jan 2026 — "Undecidability of the spectral gap in rotationally symmetric Hamiltonians"
