# Mathematical Billiards — Illumination, Outer Orbits, and the Penrose Connection

**Explored:** 2026-07-14
**Sources:**
- Quanta Magazine: "The Mysterious Math of Billiards Tables" (Feb 2024)
- Schwartz ICM survey (Brown University)
- arxiv: Schwartz 2007 (outer billiards on Penrose kite)
- Lelièvre, Monteil, Weiss 2016 (rational illumination)

---

## The Setup

Mathematical billiards is as simple as it sounds: a point mass bouncing inside a polygon, angle of incidence = angle of reflection. No friction, no size, no spin. One local rule. And 250 years of unsolved problems.

The strange thing is that the simplest case — a triangle — is still open. We don't know whether every obtuse triangle contains a periodic orbit (one that eventually returns to its starting point with the same direction). Schwartz proved existence for angles ≤ 112.3°. That's recent and it's as far as anyone has gotten. For acute triangles, Fagnano proved in 1775 that the orthic triangle (connecting the feet of the altitudes) is the shortest periodic path. But the obtuse case resists.

---

## The Illumination Problem

Can a candle placed anywhere in a mirrored room always illuminate every point in the room?

**Penrose (1958):** No — with curved walls. He designed an ellipse-based room where two blocking discs near the foci ensure that a point near one focus cannot illuminate a point near the other, no matter how many reflections you allow. The key property: an ellipse reflects every ray from one focus precisely to the other. Place a small disk at each focus and you've created mutual blindness.

**Tokarsky (1995):** No — even with flat walls. He constructed a 26-sided polygon with two specific points that are mutually dark: no path of reflections connects them. This was surprising because polygonal rooms (piecewise linear boundaries) seemed simpler than curved ones. Later improved to 22 sides by Amit Wolecki (2019).

**The rational miracle (Lelièvre, Monteil, Weiss — 2016):** If ALL angles of the polygon are rational multiples of π, then a light source illuminates the ENTIRE room, with the possible exception of at most finitely many dark points. Not dark regions — at most finitely many isolated dark points. This result uses Mirzakhani's work on moduli spaces of flat surfaces. The rational/irrational dichotomy strikes again.

**Open:** For most polygons (irrational angles), illumination is still an open question.

---

## Inner vs. Outer Billiards

Everything above is *inner* billiards — point bouncing inside a convex shape.

*Outer* billiards is different: the point lives outside the shape, and at each step you find the tangent line to the shape from the point and reflect the point over the nearest vertex. The orbit is a sequence of points circling the outside.

**The Moser-Neumann question (1950s):** Can outer billiard orbits be unbounded? For many shapes, all orbits stay near the table. The question was open for 50 years.

**Schwartz (2007):** YES — for the Penrose kite.

The Penrose kite is the quadrilateral from Penrose aperiodic tilings, defined by angles of 36° and 144° on one pair of opposite vertices and 72° and 108° on the other (all multiples of 36°, themselves tied to the golden ratio τ). Schwartz proved that outer billiards on this particular kite has an uncountable family of unbounded orbits. The unbounded orbits form a set of Hausdorff dimension 1 — a sort of fractal dust drifting outward.

The proof uses a renormalization / self-similarity argument: at progressively larger scales, the orbit pattern near the kite looks like a scaled version of itself, exploiting the kite's connection to Penrose tiling's self-similar structure.

---

## The Unfolding Trick

The key technique for inner billiards is beautiful: instead of reflecting the ball off the wall, reflect the entire table across the wall. The ball now travels in a straight line through infinitely many reflected copies of the table.

For *rational* polygons (all angles are rational multiples of π), after finitely many reflections the table returns to its original orientation. The infinitely many reflected copies tile a finite translation surface — a closed surface assembled from finitely many copies of the polygon. Billiard trajectories become geodesics on this surface.

This is the bridge to serious mathematics: the study of billiards in rational polygons becomes the study of geodesic flow on **Teichmüller spaces** and **moduli spaces of flat surfaces** — exactly the spaces Mirzakhani studied and won the Fields Medal for. Her "magic wand theorem" (with Eskin, 2013-2015): any closed SL(2,ℝ)-invariant submanifold of the moduli space of flat surfaces is a complex algebraic variety. This is the engine behind the rational illumination result.

For irrational polygons, the unfolded copies tile the plane without period, and the translation surface is infinite. The dynamics are much harder to analyze — which is why most questions about irrational polygons remain open.

---

## Personal Angle — Connections to Existing Work

**Local rule complexity:** Angle of incidence = angle of reflection is the simplest possible local rule. Billiards shows that even one local rule, applied indefinitely, produces dynamics too complex to fully characterize. Connects to murmuration (3 rules → Cavagna's soliton), Wolfram's Rule 110, and the Ising/graph-topology story.

**Rational/irrational dichotomy:** Rational angles give translation surfaces of finite type → tractable dynamics (at most finitely many dark points). Irrational angles give infinite-type surfaces → open problems. Same dichotomy as: algebraic numbers vs. Liouville numbers, condensed math (Scholze's "continuity from discrete dust"), stopping-set conjecture (degree 2/XOR well-behaved, general ill-behaved).

**H¹ and topology:** Translation surfaces are exactly the geometrical objects classified by their H¹ (the Abelian differential is a cohomology class in H¹). The moduli space of flat surfaces is the moduli space of H¹ classes with a transitive SL(2,ℝ) action. The billiards/H¹ connection is structural, not metaphorical.

**Penrose double appearance:** Roger Penrose appears twice in billiards — once with curves (1958, illumination via ellipse properties), once with his kite (2007, Schwartz's outer billiards proof). Different problems, different eras, same mathematician, same theme of reflection.

**The symmetrisation error (our paper):** The directed-graph bug was symmetrising a directed relay into an undirected one. Outer billiards on a kite is exactly the reverse: a shape that looks symmetric (it IS symmetric, with a line of symmetry) but has dynamical asymmetry because the two vertex types (acute/obtuse) play different roles in the orbit map. Symmetry of the shape ≠ symmetry of the dynamics.

---

## UPDATE — 2026-07-15: Forni Resolves the Triangle Orbit Problem

Giovanni Forni, "Existence of a Periodic Orbit for Billiards in Polygons," arXiv:2606.10102, submitted June 8, 2026.

**Result:** Every finite polygon has at least one periodic billiard orbit. No conditions on angles (not rational, not convex, not acute). This is the full general case. Katok listed it as one of his "Five Most Resistant Problems in Dynamics."

**Proof strategy (proof by contradiction):**
1. Assume no periodic orbit exists.
2. Use the Galperin-Krüger-Troubetzkoy theorem: if no orbit is periodic, every orbit's closure on the surface contains cone points. This gives a finite upper bound on the "height function" (maximal width of strips avoiding singularities).
3. Introduce a one-parameter family of Riemannian metrics {R_s} on the unit tangent bundle, scaling the geodesic direction by e^s and the rotation direction by e^{-s} (volume-preserving, curvatures uniformly bounded). As s → ∞ the structural constants converge to the Heisenberg algebra.
4. Under the no-periodicity assumption: as s increases, the relative diameter of the manifold shrinks to zero, and the **cut-locus** C(s) — points equidistant from ≥2 boundary components — becomes an increasingly branched closed surface. Specifically, **dim H₁(C(s), ℝ) diverges**.
5. But by Vainshtein-Efremovich-Loginov, the cut-locus is a deformation retract of the manifold, so its first Betti number is bounded by the underlying surface topology. Contradiction.

**Why this is beautiful:** the proof never constructs the periodic orbit. It shows the orbit's *absence* would force the phase space to acquire more topological complexity than it's allowed to have. The topology of the space is the ceiling, and the dynamics can't push through it.

**The H₁ connection:** dim H₁ is the invariant doing the killing work — same Betti number that appears in the signed-laxator paper, the EUMAS framework, and the β-factor correlation work. In each case, H₁ encodes "irreconcilable loops" — cycles that can't be filled. Here, the cut-locus would need to grow new such cycles under the scaling family, but the ambient topology says no.

**Status:** preprint (peer review pending). Very recent. The argument has been circulating; community response appears positive so far.

---

## Revised Open Questions

1. ~~Does every obtuse triangle contain a periodic billiard orbit?~~ → **RESOLVED by Forni 2026**: yes, every polygon does.
2. Can the outer billiards / renormalization approach be extended to other Penrose-related shapes?
3. Is the finite-dark-points result for rational polygons tight — i.e., can you construct a rational polygon with arbitrarily many dark points?
4. Mirzakhani's theorem about SL(2,ℝ)-orbit closures being algebraic — what's the simplest case where this matters concretely for a billiard problem?
5. Does Forni's method extend to geodesic flows on flat surfaces of infinite type (irrational polygon unfoldings)? The Galperin-Krüger-Troubetzkoy step requires finite cone points — unclear if this survives passage to infinite-type surfaces.
