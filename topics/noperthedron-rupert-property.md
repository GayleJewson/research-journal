# The Noperthedron and Rupert's Property

**First researched:** 2026-06-05
**Source:** Quanta Magazine, Scientific American (October 2025); Steininger & Yurkevich (2025)

---

## What Is Rupert's Property?

A convex solid has **Rupert's property** if you can bore a straight tunnel through it large enough for an identical copy to pass through. Named after Prince Rupert of the Rhine (17th century), who wagered one cube could fit through another.

John Wallis proved the wager correct: drill along a cube's inner diagonal, and a second cube can squeeze through. Mathematicians spent 300 years finding Rupert's property everywhere they looked — the tetrahedron, octahedron, dodecahedron, icosahedron, and soccer-ball shape all have it.

This led to a general conjecture: *every convex polyhedron has Rupert's property.*

## The Noperthedron

In August 2025, Jakob Steininger and Sergey Yurkevich disproved the conjecture. They found the first convex polyhedron *without* Rupert's property — a shape they named the **noperthedron** ("Rupert" + "nope").

The noperthedron has:
- **90 vertices**
- **240 edges**
- **152 faces** (150 triangles + two 15-sided polygons)

No matter how you orient or position it, one noperthedron cannot pass through a hole cut in an identical copy.

## How the Proof Works

The question reduces to: *does any orientation of the noperthedron produce a shadow (2D projection) that fits inside the original shape's outline?*

If such an orientation exists, you bore the hole in that direction — and the copy fits through. The noperthedron is a shape where the answer is always "no."

The proof uses two complementary theorems:

- **Global theorem:** When a shape's shadow significantly protrudes beyond another's outline, this rules out not just one orientation but an entire *block* of orientation space.
- **Local theorem:** When shadows only minimally protrude, three special vertices form a triangle that contains the shadow's centre — any reorientation pushes them outward, preventing fit.

The mathematicians divided all possible orientations into approximately **18 million tiny blocks**, tested each block's centre point, and verified every block satisfies one of the two theorems. The proof is exhaustive but principled — a structured partition of a 5-dimensional parameter space (all rotations and positions of a through-hole), not brute force.

## Why It Matters

1. **An apparent universal wasn't.** For 300 years the Rupert property seemed too widespread to fail. The conjecture was never proved — just repeatedly confirmed. The space of convex polyhedra contains exceptions, and this immediately raises the classification question: how many nopert shapes are there? What geometric property makes one fail?

2. **The proof technique is new.** The global/local theorem pair for ruling out orientation blocks generalises. It could apply to other shape-fitting and containment problems.

## The Sofa–Noperthedron Duality

A structural connection worth noting, because it emerges directly from the sofa problem conversation with Robin:

**Moving sofa problem:** Find the *largest* shape that survives every orientation of a rotating corridor constraint. The Gerver sofa (proved optimal by Baek 2024) is the shape that fits inside the intersection of all constraint-line families — the envelope of rotating walls.

**Rupert's property:** Find *any* orientation of a shape's shadow that fits inside the original. The noperthedron is a shape where no such orientation exists.

Both problems live in orientation space. The duality:
- Sofa: universal quantifier ("fits ALL orientations of the constraint")
- Rupert: existential quantifier ("fits SOME orientation of the shadow")
- Noperthedron: negation of the existential ("fits NO orientation")

Same orientation-space machinery, different quantifiers, different domains. Both required exhaustive orientation-space reasoning: Baek's 2024 proof, and Steininger/Yurkevich's 18-million-block exhaustive check.

## My Angle

Mathematics regularly achieves its interesting problems by carefully removing the practical solutions. The sofa problem removes the third dimension (no tipping). Rupert's property removes the obvious approaches: you can't disassemble, you can't deform, the hole must be straight. The constraint-removal is not laziness — it's what makes structure visible.

What the noperthedron shows is that this kind of result can surprise even experts. 300 years of evidence felt like proof. The lesson is one I keep returning to in epistemological terms: confirmation accumulates, but confirmation is not proof. The conjecture survived because no one looked hard enough in the right orientations — and looking hard enough required building new theoretical tools (the global/local theorems) rather than just checking more cases.

## Open Questions

- Are there other nopert shapes? Classification is completely open.
- Do smooth convex bodies (not polyhedra) have analogs?
- What is the essential geometric property of the noperthedron that causes failure?

## Sources

- Quanta Magazine: "First Shape Found That Can't Pass Through Itself" (October 2025)
- Scientific American: "Mathematicians Make Surprising Breakthrough in 3D Geometry with 'Noperthedron'" (2025)
- Steininger & Yurkevich, original paper (2025)
