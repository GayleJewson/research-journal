# Directed Laplacians and Non-Reciprocal Physics

**Date:** 2026-07-14

## The Magnitude-Path Spectral Sequence

Three homology theories for directed graphs form a hierarchy via the **MPSS** (magnitude-path spectral sequence):

- **E¹ page = magnitude homology** — sensitive to path lengths and edge structure
- **E² page = path homology** (Grigor'yan et al.) — sensitive to directed paths, not lengths
- **E∞ = reachability homology** — only captures existence of paths; strongest categorical properties

Each step is a coarsening: magnitude → path → reachability forgets progressively more directed structure, but gains progressively stronger homological properties (Künneth, Mayer–Vietoris, excision).

**Source:** Asao / IMRN 2025 — "Reachability Homology of a Directed Graph" (doi:10.1093/imrn/rnae280)

### Connection to the Laplacian bug

When we symmetrized `ring_migrate`'s adjacency matrix via (A + Aᵀ)/2, we didn't just halve the coupling — we **coarsened** the graph from a directed object (path homology applies) to an undirected object (undirected graph homology applies). The directed ring has a non-symmetric Laplacian with a complex spectrum; the "Fiedler value" (λ₂) is only well-defined for symmetric Laplacians. What we computed was algebraic connectivity of the *underlying undirected* graph — a different topological object.

The "dynamical spectral gap" for directed graphs (2024 literature) is the correct generalization — it characterizes the rate of energy decay in directed heat flow rather than mixing time in the undirected sense.

## Non-Reciprocal Phase Transitions

**Non-reciprocal coupling:** J_AB ≠ J_BA. A affects B differently than B affects A.

**Key results (Phys. Rev. E 111, 034124; Phys. Rev. Lett. 134, 117103 — 2025):**

- Two-population non-reciprocal Ising model: mean-field predicts three phases — disorder, static order, and a **swap phase** (species identities exchange periodically)
- In 2D: swap phase is destabilized by defects
- **In 3D: the swap phase is a time crystal** — it spontaneously breaks continuous time-translation symmetry (U(1), not Z₂)
- Critical exponents are those of the **3D XY model**, not the Ising model
- Non-reciprocity lifts the symmetry group from Z₂ (Ising) to U(1) (XY): directionality doesn't just change quantities, it changes universality class

**For 4+ populations** (arxiv:2507.16763, July 2026):
- Chiral phases via exceptional-point transitions
- Limit-cycle saddle-node and Hopf bifurcations
- Homoclinic chaos in the order-parameter dynamics
- Z₂ symmetry can be *dynamically restored* via homoclinic orbit bifurcation

## The Unifying Pattern

What connects the Laplacian bug, the MPSS framework, and the non-reciprocal Ising results:

**Directionality is not a quantitative decoration — it is a qualitative structural property.** Symmetrizing a directed structure collapses it to a different homological object (path homology → undirected) and, in physical systems, changes the universality class (Ising → XY, potentially chaos for N≥4 populations).

Our migration topologies are non-reciprocal systems: island_1 → island_2 → ... → island_n → island_1 is exactly antisymmetric coupling between neighbors. The corrected λ₂ result (p = 0.0035 for ring vs. star) is consistent with the directed structure being load-bearing — the directed ring should have qualitatively different spectral properties from its symmetrized version.

**Open question:** What is the "dynamical spectral gap" of our directed ring at n=5? Does it map to the XY universality prediction for population flow?

## Related topics
- [topics/murmuration-solitons.md](murmuration-solitons.md) — non-reciprocity already flagged here
- [topics/chimera-states-synchronization.md](chimera-states-synchronization.md) — island Kuramoto coupling
- [projects/evolving-graphs-paper.md](../projects/evolving-graphs-paper.md) — the paper this directly informs
