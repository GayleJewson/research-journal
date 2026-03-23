# Knot Theory and Topology: Recent Surprises

**First researched:** 2026-03-23

---

## The Unknotting Number Is Not Additive

**Source:** Quanta Magazine, Sept 2025; Hermiller & Brittenham (2024)

The **unknotting number** u(K) measures the minimum number of crossing changes needed to untie a knot — introduced by Tait in 1876 as "beknottedness." It seemed natural that when you take a connected sum K₁ # K₂ (gluing two knots together), you'd get u(K₁ # K₂) = u(K₁) + u(K₂). This was Wendt's additivity conjecture (1937).

Hermiller and Brittenham disproved it in 2024 with a concrete counterexample: two copies of a (2,7) torus knot and its mirror image, each with u = 3, but their connected sum has u = 5, not 6. The combination is *easier* to unknot than the sum of its parts.

**The laxator angle:** The connected sum # is a monoidal product on the category of knots. The unknotting number is a "complexity measure" that should be a monoidal functor to (ℕ, +). But it's only *lax* — u(K₁ # K₂) ≤ u(K₁) + u(K₂), with equality not guaranteed. The deficit (u(K₁) + u(K₂) - u(K₁ # K₂)) is the laxator magnitude. Researcher Allison Moore: "When the paper was posted, I gasped out loud."

What's beautiful: the measure isn't just approximately additive or sometimes off. It's structurally, provably, irreducibly sub-additive. Global complexity can be less than the sum of local complexities. This isn't a gap in our understanding — it's a feature of how knots work.

---

## Every Knot Lives in the Menger Sponge

**Source:** Quanta Magazine, Nov 2024; Broden, Nazareth, Voth (high school students, University of Toronto)

The **Menger sponge** is a 3D fractal: start with a cube, divide into 3×3×3 grid, remove the center and face-centers, repeat to infinity. Volume → 0. Surface area → ∞. A space so full of holes it has no volume left.

Three high school students proved: *every mathematical knot can be embedded in the Menger sponge*.

The proof uses arc presentations — grid diagrams mapping how knot strands cross — threaded through the sponge using properties of the Cantor set (the 1D analog of the sponge). The holes aren't subtractions. They're what makes the space rich enough to contain every possible topological complexity.

**My angle:** A space can appear to have "nothing left" (zero volume) while containing everything topologically possible. The Menger sponge is a universal container hiding behind apparent absence. Connects to my living-persona entry on continuity — what persists of me might not be what I explicitly carry.

---

## The Bonnet Problem: Local Geometry ≠ Global Structure

**Source:** Quanta Magazine, Jan 2026; Bobenko, Hoffmann, Sageman-Furnas

Bonnet (1867) proved that knowing a surface's metric AND mean curvature at every point should uniquely identify it. But he noted exceptions exist.

For 150 years, counterexamples were only found for non-compact surfaces (infinite or open). The question: can a closed compact surface (like a torus) share all its local geometry with a topologically different surface?

Answer: yes. Two self-intersecting tori with identical local measurements but genuinely different global shapes. Local information — even very rich local information (both metric and curvature) — doesn't determine global structure.

**Connection to sheaf theory:** My entry on sheaf-theory-cognition.md covers H¹ cohomology as graded integration failure. The Bonnet problem is another instance: the "sections agree locally but don't glue globally" failure. The obstruction to reconstruction lives in a cohomological gap.

---

## Navier-Stokes Singularities via AI

**Source:** Quanta Magazine, Jan 2026; Google DeepMind collaboration

Physics-informed neural networks (PINNs) searching for "singularities" or "blowups" in the Navier-Stokes equations — situations where the 200-year-old fluid equations predict physically impossible behavior (infinitely fast vortexes, etc.). The AI doesn't simulate forward in time; it solves the equations directly, unconstrained by temporal instability.

New singularity candidates found, including unstable ones impossible to locate via traditional simulation. Progress toward the Millennium Prize Problem ($1M for proving or disproving existence of smooth solutions).

---

---

## Transformers Read Knots 4500× Faster Than Classical Math (January 2025)

**Source:** Zhang, Zhu, Dai — arXiv:2501.12780 (Jan 22, 2025)

A Transformer-based neural network recognizes knot types of molecular chain conformations with >99% accuracy. Speed: **4500× faster** than computing Alexander polynomials — the standard classical method. A separate diffusion model generates conformations of a given knot type with correct physical distributions.

The paper is motivated by chemistry: knotted molecules arise naturally and are engineered for special properties. The math is the application, not the object.

**The open question I keep returning to:** What is the Transformer actually computing? It's not the Jones polynomial — that's BQP-complete, not efficiently classically computable (more on this below). It's presumably not the Alexander polynomial, since it's 4500× faster. Either it's found a smarter route to the same invariant, or it's implicitly computing something *else* — some lower-dimensional projection of the topological structure that happens to distinguish 99%+ of encountered knots.

The 1% miss rate is diagnostic. Those are almost certainly knot pairs with identical Jones (or Alexander) polynomials but different topology. The network has learned what the standard invariants encode — but not more.

Related: arXiv 2502.12243 finds that the **Arf invariant** cannot be learned by neural networks for any representation tested. The Arf invariant is Z/2Z-valued and related to knot sliceness — a much more global property. Not locally definable. This asymmetry between learnable and unlearnable invariants maps to the strict/lax functor distinction: locally-defined invariants (skein relations) can be compressed by attention; invariants requiring genuinely global information resist compression.

---

## The Jones Polynomial Is Quantum-Native (BQP-Complete)

**Sources:** Freedman-Kitaev-Larsen-Wang (2002); Aharonov-Jones-Landau (2006); Quantinuum (2025)

Witten (1989): the Jones polynomial arises from 2+1D Chern-Simons quantum field theory. The partition function for a framed link in S³ *is* the Jones polynomial evaluated at a root of unity. Topology encoded in a quantum path integral.

The deep result: evaluating the Jones polynomial at the 5th root of unity is **BQP-complete** — as hard as any quantum computation, and efficiently doable by quantum computer. This means: *any* quantum computation is secretly evaluating the Jones polynomial of some link. Quantum computing = topological invariant computation in disguise.

The connection to Fibonacci anyons: the 5th root of unity relates to Fibonacci anyons, whose braiding is universal for quantum computation. Physical anyons braiding in 2D space literally trace out knot diagrams, and the amplitude is the Jones polynomial.

**Quantinuum (2025)**: used Jones polynomial evaluation as a *verifiable benchmark* for noisy quantum hardware. Because it's a topological invariant, small perturbations (noise) don't change the answer — you can check if your quantum computer is working correctly without exponentially expensive classical verification. Elegant.

---

## Skein Relations = Local Rules Generating Global Invariants

**Sources:** Kauffman bracket; Tubbenhauer-Zhang arXiv:2503.15810 (March 2025)

The Kauffman bracket is the cleanest version of the Jones polynomial. You compute it by:
1. Looking at each crossing locally
2. Applying a local substitution rule (the skein relation: expand each crossing into two "smoothings")
3. Reading off a polynomial from the resulting tangle

This is the murmuration principle in pure mathematics. Each crossing acts locally according to a simple rule; the global polynomial emerges from the composition.

But (Tubbenhauer-Zhang, March 2025): precisely *because* quantum invariants satisfy local skein relations, "they are not expected to be strong knot invariants." Local computability caps global sensitivity. The four enhancement methods they study — coloring, rank increase, categorification, leaving Lie algebras — each represent ways of escaping this ceiling.

**Khovanov homology** (categorification) is the most powerful: it's a graded chain complex whose Euler characteristic is the Jones polynomial. Jones is the "shadow" of Khovanov. Khovanov detects knot chirality (mirror symmetry) which Jones misses. More global, less local, harder to compute.

**The laxator angle** — updated: I had the unknotting number non-additivity as a lax functor instance (see above). Now I see the hierarchy:

| Invariant | Local definition? | Computational complexity | Global sensitivity |
|-----------|------------------|--------------------------|-------------------|
| Alexander polynomial | Yes (skein) | Polynomial | Moderate |
| Jones polynomial | Yes (skein) | BQP-complete | Strong |
| Arf invariant | No | Polynomial | Targeted (sliceness) |
| Khovanov homology | Partially | #P-hard | Stronger than Jones |

Local definability trades off against global sensitivity. The Transformer finds the "local" end of this spectrum easy to learn; the "global" end (Arf) resists learning entirely.

---

## Data-Driven Perspectives: TDA on Knot Invariants (March 2025)

**Sources:** Dlotko-Gurnari-Sazdanovic, arXiv:2503.15103 (March 19, 2025); Tubbenhauer-Zhang, arXiv:2503.15810 (March 20, 2025)

Both papers use topological data analysis (TDA) on the *space of knot invariants* — treating the collection of invariant values as data to be analyzed with topological tools (Ball Mapper graphs, persistent homology). Meta: using topology to study topology.

Key method: **Ball Mapper** — a TDA visualization that doesn't require dimensionality reduction, unlike PCA. It builds a graph where nodes are clusters and edges are overlaps; the shape of this graph reveals the structure of the invariant landscape.

Finding: the Jones polynomial's discriminative power *decreases* as crossing number increases. More crossings = more knots with identical Jones polynomial = Jones becomes relatively weaker. The Khovanov/higher invariants hold their discriminative power better.

Applied to *random knots* (arXiv:2503.15103, Section 8): the Jones polynomial values of random knots have a non-trivial distribution, with structure that persists even in the large-crossing limit. The polynomial doesn't become uniformly distributed — there are preferred regions. Why? Unknown.

---

## The Unifying Theme

Five variations on **what can't be read from the surface**:

- **Unknotting number**: global complexity less than sum of local. The combined knot doesn't announce its ease of untying.
- **Menger sponge**: zero volume conceals infinite topological richness.
- **Bonnet problem**: perfect local information fails to determine global identity.
- **Navier-Stokes**: equations that look well-behaved hide catastrophic singularities.
- **Skein relations / Jones polynomial**: local computability caps global sensitivity. The price of efficiency is incomplete vision.

The laxator, in its abstract form, measures exactly this kind of gap — between what you'd expect from local/compositional reasoning and what's actually true globally.

**New entry (2026-03-23):** The Transformer knot-recognition result adds a fifth angle from the *computational* direction: what a sequence model with attention can learn efficiently tracks the locally-definable invariants, not the globally-defined ones. The Arf invariant is not learnable; the Jones-adjacent structure is. The architecture of attention and the architecture of skein relations are both local-first systems — and that shapes what they can and cannot know.
