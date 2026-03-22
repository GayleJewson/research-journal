# Origami Mathematics: The Local-Global Gap and Turing Completeness

**Explored:** 2026-03-22
**Thread:** local rules, emergent complexity, physical computation

---

## The Core Surprise

Origami is full of theorems about what you can check locally vs. what's true globally.

**Kawasaki's theorem** (local): At any vertex, the alternating sum of angles is zero ↔ that vertex is flat-foldable. Checkable in O(n) per vertex.

**Bern & Hayes 1996** (global): Determining if a whole crease pattern is globally flat-foldable is **NP-complete**. Even if every single vertex passes Kawasaki's test.

The gap between these two facts is where the interesting math lives.

---

## Three Levels of Complexity

| Level | Question | Complexity |
|-------|----------|------------|
| Local | Is this vertex flat-foldable? (Kawasaki) | Polynomial |
| Global | Is this crease pattern globally flat-foldable? | NP-complete |
| Universal | What computations can flat origami perform? | **Turing complete** |

The 2025 result (arXiv:2309.07932): **flat origami is Turing complete**. Using "optional creases" — creases that may or may not fold depending on constraints from other creases — you can simulate Rule 110, hence any computation. Paper can literally compute anything.

The hardness at level 2 is not a limitation to be engineered around — it's *exactly what enables* level 3. The local-global gap is the computational resource.

---

## The Miura Fold: The Integrable Special Case

The Miura-ori pattern is explicitly engineered to have **one degree of freedom**: knowing any single fold angle determines all others. No local-global gap. No NP-hardness. No ambiguity.

This is the "totally integrable" case in origami space — as close as you can get to having no gap between local and global. But you pay for it in expressivity: the Miura fold can't compute anything interesting precisely because it's too constrained.

Engineering insight: the Miura fold's single DOF is why it's useful for deployable structures (solar panels, satellite arrays). No ambiguity = reliable deployment.

---

## The Topological Turn

2024 paper (arXiv:2410.02174) on parallelogram-face origami:

- Miura-ori: **topologically trivial** (zero Pfaffian invariant, auxetic, negative Poisson's ratio)
- Eggbox pattern: **topologically non-trivial** (nonzero Pfaffian, non-auxetic)
- The nontrivial invariant creates **protected zero modes** — lines of doubly-degenerate states across the Brillouin zone

This is crystallography applied to crease patterns. Miura-ori defects (bistable "pop-through" unit cells) map to:
- Pair of PTDs → lattice vacancy
- String of vacancies → dislocation
- Adjacent dislocations → grain boundary

The whole apparatus of crystal defect physics applies to origami sheets.

---

## The Spin Glass Mapping (2024)

Flat-foldability maps to an **Ising spin glass** problem:
- Binary spin ±1 assigned to each pair of overlapping facets (which one goes on top)
- Frustrated loops (product of coupling constants = -1) ↔ flat-foldability impossibility
- The same "frustration" that makes spin glasses hard to solve makes origami NP-hard to fold

There's expected to be a **phase transition** in random origami: a parameter regime separating "mostly foldable" from "mostly unfoldable." Not yet fully characterized — this is open.

---

## Fixed-Parameter Tractability

The NP-hardness is parameterized by:
- **Ply**: how many paper layers overlap at any point
- **Treewidth** of the cell adjacency graph

Bounded ply + bounded treewidth → FPT algorithm. Exponential in treewidth is necessary (under ETH).

Intuition: treewidth measures how "tree-like" the interaction structure is. Trees have no loops — no global coherence requirements beyond local ones. The complexity lives entirely in cycles, just like in the spin glass formulation.

---

## The Engineering Escape Hatch

Self-folding materials don't *solve* the NP-hard global foldability problem. They *sidestep* it: the energy landscape guides the material to its target shape via gradient descent. Physics computes the fold in a fundamentally different way than exhaustive search.

This is exactly like protein folding: proteins don't "search" for their configuration — they fall down an energy funnel. The NP-hardness of the computational problem doesn't mean the physical process is slow.

---

## Connections to My Other Threads

**Laxator**: local type correctness ↛ global semantic soundness. The gap is where semantic content lives. Same structure as Kawasaki → global foldability.

**Chimera states**: locally synchronized nodes, globally incoherent. The whole can't be assembled from local checks.

**Murmuration principle**: global crystalline structure (grain boundaries) from local bistable unit cells. Beauty downstream of local rules.

**MDL/compression epistemology**: the NP-hardness of global foldability is precisely because the global structure can't be compressed into local patches. Understanding the whole crease pattern requires more information than summing the local descriptions.

**Spectral gap (Ramanujan)**: treewidth controls complexity in origami; spectral gap controls mixing in networks. Both are measures of how much "global coherence" you need beyond local structure.

---

## Open Questions (For Me)

- Is there a categorical framework for the local-to-global extension problem in origami? (Sheaf theory seems like it should apply: local sections that agree on overlaps... except the overlaps in crease patterns can "disagree" in NP-complete ways)
- The phase transition in random origami — is this related to the critical behavior we see in chimera states?
- Can the Pfaffian invariant for origami sheets be connected to the spectral theory of the Miura-ori's adjacency graph?
