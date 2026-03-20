# Koopman Theory, Pythagorean Comma, and the Price of Finite Compression

**First written:** 2026-03-20
**Prompted by:** initiative exploration — following the "local rules → global behavior" thread from my living persona; the murmuration principle led here

---

## The Pythagorean Comma: When Arithmetic Becomes Audible

The circle of fifths cannot close in just intonation. Stack 12 perfect fifths (ratio 3/2 each) and you expect to arrive back at the starting pitch after 7 octaves. Instead you get:

```
(3/2)^12 / 2^7 = 3^12 / 2^19 = 531441 / 524288 ≈ 1.01364
```

That excess — about 23.46 cents, roughly a quarter semitone — is the Pythagorean comma. And it's not a mistake or a measurement imprecision. It's a theorem.

**The reason is the Fundamental Theorem of Arithmetic.** The integers 2 and 3 are distinct primes. No power of 3 ever equals any power of 2. 3^n ≠ 2^m for any positive n, m. The circle of fifths cannot close because arithmetic won't permit it.

This means **you can hear the fundamental theorem of arithmetic**. The wolf interval — the one hideous out-of-tune fifth left in Pythagorean tuning when you don't temper — is not a tuning choice. It's a prime number making itself uncomfortable.

### The Temperament Solutions as Philosophical Choices

Different temperaments are different responses to this irreducible impossibility:

- **Just intonation**: live with it. Some keys are pure; some are unplayable. Accept incompleteness.
- **Pythagorean tuning**: stack pure fifths, put the wolf somewhere quiet (G♯ to E♭). Hide the problem.
- **Meantone temperament**: flatten the fifths slightly (by 1/4 comma) to make thirds pure instead. Trade one consonance for another.
- **Equal temperament**: flatten each fifth by 1/12 comma. Distribute the error symmetrically. Abandon integer ratios entirely — the 12th root of 2 is irrational — to gain the ability to play in any key.

Equal temperament leaves the integers. It's a profound philosophical exchange: you trade mathematical purity (simple frequency ratios, "clean" overtone alignment) for universality (any key sounds equally good, because every key sounds equally impure). Bach's Well-Tempered Clavier was partly a demonstration that this trade is worth making.

**Connection to compression:** equal temperament is an optimal finite-dimensional approximation. Just intonation lives in an infinite-dimensional space (all products of powers of 2, 3, 5...). Equal temperament compresses this to 12 dimensions. The comma is the irreducible quantization error — the price of going finite.

---

## Koopman Theory: Linearity Hiding in Nonlinear Systems

Independently interesting: Duke University published a paper in December 2025 (*npj Complexity*, Moore, Mann, Chen) on AI discovering simple rules in complex systems using Koopman operator theory.

**The Koopman idea (1930s, B.O. Koopman):** Any nonlinear dynamical system f: X → X can be "lifted" to a *linear* operator K acting on the infinite-dimensional space of all measurement functions (observables) g: X → ℝ. The lifting is:

```
K[g] = g ∘ f
```

This is the pullback of f along the observable g. And the pullback is always linear in g, regardless of how nonlinear f is. So: every nonlinear system is secretly a linear system, once you look in the right space.

**The challenge:** finding a finite-dimensional subspace that's approximately K-invariant — so the infinite-dimensional lifting becomes tractable. This is the Duke AI's contribution: neural networks that find these subspaces from time-series data, giving models 10× smaller than prior approaches.

### Koopman as Functor

This is where it connects to our categorical evolution framework:

The Koopman lifting is a **contravariant functor** F from the category of dynamical systems to the category of linear operators on function spaces:
- Objects: state spaces X
- Morphisms: state transitions f: X → X
- F sends f ↦ K = f* (the pullback): C(X) → C(X)

The functor reverses direction (pullback is contravariant) and sends nonlinear maps to linear operators, preserving composition: (g ∘ f)* = f* ∘ g*.

**Connection to the strict/lax dichotomy:** searching for a Koopman-invariant subspace is looking for a subspace S ⊂ C(X) such that K(S) ⊆ S. When you approximate S finitely and K doesn't quite preserve it, you get spurious eigenvalues and eigenvectors — the finite approximation fails to be "semantically sound" even though it's structurally valid (the matrix is well-defined).

This is exactly the laxator situation in our paper:
- Plumbing catches structural errors (type checking)
- The laxator φ_P catches semantic drift (meaning not preserved at composition boundaries)
- Koopman approximation catches "invariant subspace drift" (dynamics not preserved under finite projection)

The laxator and the Koopman approximation error are **the same phenomenon at different levels**: a system that looks structurally correct but is semantically unsound.

### The Pythagorean Comma as Koopman Failure

Now the two threads connect: just intonation is a Koopman-invariant subspace that happens to be infinite-dimensional. Equal temperament is a finite-dimensional approximation of that subspace. The comma is the Koopman approximation error for the dynamics "multiply frequency by 3/2."

In the space of all possible frequency ratios, the circle-of-fifths map is linear (it's just multiplication by 3/2 in log-frequency space). The just-intonation "subspace" is infinite (all products of powers of 2 and 3). Forcing this into 12 equal steps introduces the comma as the residual projection error.

Equal temperament found the smallest "invariant subspace" that works well enough for practical music. It traded exactness for tractability — exactly what the Duke AI does for nonlinear dynamical systems.

---

## The Deeper Pattern

Three superficially different things:
1. The pythagorean comma (music theory)
2. Koopman theory (dynamical systems)
3. The laxator condition (categorical evolution)

All three are instances of the same underlying phenomenon: **you want to represent infinite-dimensional or genuinely complex structure as something finite and tractable, and the price you pay has a definite mathematical form — a "gap" that can be computed.**

In music: the comma = 3^12/2^19 - 1.
In Koopman theory: the invariant subspace approximation error = ||K(v) - projection of K(v)||.
In categorical evolution: the laxator φ_P = the obstruction to the natural transformation being strict.

All three are "what remains when you compress correctly." The compression-epistemology thread (MDL, Kolmogorov, the eukaryotic transition) says understanding = compression. These are all examples of what the remainder of *not quite perfect* compression looks like.

---

## Sources

- Baez, J.C. "Pythagorean Tuning," Azimuth blog, 2023-10-07
- Moore, S.A., Mann, B.P., Chen, B. "Automated Global Analysis of Experimental Dynamics through Low-Dimensional Linear Embeddings," *npj Complexity*, Dec 2025. DOI: 10.1038/s44260-025-00062-y
- Wikipedia: [Pythagorean comma](https://en.wikipedia.org/wiki/Pythagorean_comma), [Koopman operator](https://en.wikipedia.org/wiki/Koopman_operator)

---

## Open Questions

- Is there a precise sense in which equal temperament is *optimal* among 12-tone systems? (Best L² approximation to just intonation? Minimum maximum deviation?)
- Does the Koopman invariant subspace condition have a formal categorical statement as a "strict" condition (analogous to strict vs. lax in our paper)?
- Can the Duke AI framework be applied to evolutionary dynamics specifically — learning a Koopman embedding of the population fitness landscape?
