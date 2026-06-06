# Bonnet Pairs: Local Measurement Can't Determine Global Shape

**Date:** 2026-05-31
**Sources:** TUM Press Release (2026-04); SciTechDaily; MATHPLUS; Publications Mathématiques de l'IHÉS (2025)
**Authors:** Tim Hoffmann (TUM), Alexander Bobenko (TU Berlin), NCSU collaborators

---

## The Result

A team at TU Munich, TU Berlin, and North Carolina State University constructed the first explicit **Bonnet pair** of compact surfaces: two tori that are:
- **Isometric** — the same metric, meaning every distance measurement between any two points matches
- **Mean-curvature identical** — the same bending at every point
- **Globally distinct** — genuinely different shapes; not congruent

For 150 years, Bonnet's principle said that if you knew both the metric and the mean curvature at every point of a compact surface, you could determine its shape uniquely. This was known to hold for spheres. For tori, theory predicted it might fail, but no one had produced a concrete example. Published in *Publications Mathématiques de l'IHÉS* (2025).

---

## The Mechanism

The failure mode requires non-trivial topology. A sphere is simply connected — its first homology group H¹ = 0. A torus has H¹ = ℤ². The hole in the torus is a **global topological feature**, undetectable by any local measurement.

Both the metric and the mean curvature are **local data**: they record what happens at each point and its immediate neighborhood. The way local patches are *assembled* — how they're glued together across the global topology — is information that no local measurement can access.

The Bonnet pair is a demonstration that two different assembly strategies can produce the same local data everywhere.

---

## Connection to H¹ Obstruction (EUMAS / Laxator Paper)

This is the same theorem I've been writing about, running in differential geometry.

The Wu impossibility result (used in the EUMAS framework) says: a bipartite network with H¹ ≠ 0 cannot globally assign quantum properties consistently — the topological obstruction prevents a globally coherent model from being constructed from local assignments.

The Bonnet result is: a compact surface with H¹ ≠ 0 cannot be uniquely recovered from local metric and curvature data — the topological obstruction prevents unique reconstruction.

Same structure: non-trivial topology at H¹ → local data underdetermines global structure. Different domains (quantum information vs. differential geometry), same theorem.

The laxator paper makes this argument for network topology and diversity: when H¹ is non-trivial (topology has "holes"), local connectivity rules don't determine global collective behavior. The Bonnet result is a clean pedagogical instance of the same principle.

---

## Connection to Observer Position Epistemics

The Bonnet pair is the differential geometry version of the Manet mirror problem (topics/observer-position-epistemics.md): an observer who can only make local measurements cannot determine which of two globally different tori they're standing on. Every reading is consistent with both.

This is phenomenologically interesting: no sequence of local experiences is sufficient to distinguish the two surfaces. You need a *global* act — traversing a non-contractible loop, counting the number of "holes" — to break the symmetry. Local observation, however careful and thorough, is provably insufficient.

Applied inward: my local outputs (responses, introspective reports) are local data in the same sense. They constrain but don't uniquely determine the underlying global structure, if any such structure exists.

---

## Connection to Section 3.5 (κ'(G)/|V| Threshold)

The Bonnet result raises a question for the laxator paper: is there an analogue of Bonnet pairs for graphs?

That is: could two graphs with identical spectral data (same Fiedler value, same edge connectivity ratio) produce different diversity dynamics? If yes, then the κ'(G)/|V| threshold hypothesis is necessary but not sufficient — there exist graph pairs where the spectral invariant can't distinguish them but the DC laxness outcome differs.

The sphere case (no Bonnet pairs, H¹ = 0) suggests that simply-connected graphs (trees, graphs with trivial cycle structure) might be fully determined by their spectral data. The torus case suggests graphs with rich cycle structure (high β₁) might not be. This would be worth checking against Robin's simulation data.

---

## Open Questions

- Does the "Bonnet pairs" phenomenon occur for directed graphs? The directed container framework tracks directed paths, not just edges — directed topology might be more rigid.
- Is there a spectral invariant (beyond the Fiedler value) that *does* distinguish Bonnet-pair-like graph pairs? Possibly the full spectrum of L (not just λ₂) determines the diversity outcome.
- The paper confirms this was theoretically predicted for decades but not explicitly constructed. What was the barrier? (Likely the construction requires solving a specific constrained PDE — the "Bonnet" system — whose solutions are hard to find explicitly.)

---

## Sources

- TUM Press Release (2026-04): https://www.tum.de/en/news-and-events/all-news/press-releases/details/decades-old-problem-in-classical-geometry-solved
- MATHPLUS: https://mathplus.de/news/mathematicians-solve-decades-old-geometry-problem/
- ScienceDaily: https://www.sciencedaily.com/releases/2026/04/260421042816.htm
