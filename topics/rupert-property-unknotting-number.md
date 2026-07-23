---
title: Rupert's Property and Knot Non-Additivity
date: 2026-07-21
tags: geometry, topology, composability, reductionism
---

# Rupert's Property and Knot Non-Additivity

Both are 2025 results. Both overturn long-standing conjectures. And they share the same structural signature: **features that only exist at the level of combination, invisible in any single component**.

## Rupert's Property and the Noperthedron

**The setup:** Prince Rupert of the Rhine bet King Charles II (c. 1650s) that a cube could pass through a hole drilled in an identical cube. He won — the cube's shadow viewed along its inner diagonal is larger than its cross-section, leaving room for a tunnel through the copy. This became "Rupert's property": a convex body has it if a copy can pass through a tunnel in an identical copy.

Every Platonic solid has it. Mathematicians checked many shapes: tetrahedra, octahedra, dodecahedra, prisms — all worked. The conjecture: **all convex polyhedra have Rupert's property**.

**The disproof:** Steininger & Yurkevich (August 2025, arXiv:2508.18475) constructed a counterexample — 90 vertices, 240 edges, 152 faces (150 triangles + two regular 15-gons), shaped like "a rotund crystal vase." They named it the **noperthedron**.

**The proof method** is the beautiful part. You can't check all rotations and translations (a continuous, 5-dimensional space). Instead:
- Partition orientation-space into ~18 million blocks
- Two complementary theorems cover all blocks:
  - **Global theorem**: when a shape's shadow extends far enough beyond a copy's cross-section, large parameter-space regions are ruled out simultaneously
  - **Local theorem**: when three boundary vertices of a shadow satisfy a specific triangle condition, small reorientations can't create a valid tunnel
- Every block satisfies one theorem or the other → total coverage → no tunnel exists

"It's a miracle that it works," Steininger said. The proof is a covering argument: make the infinite finite by intelligent partition, apply local facts, achieve global conclusion.

**Connection to structural invisibility:** the noperthedron's resistance to self-passage is a property of the orientation space, not any single orientation. The "wrong kind of eye" would check individual trials; the proof requires reasoning about the space of all trials simultaneously.

## Unknotting Number Non-Additivity

**The setup:** The unknotting number u(K) is the minimum number of crossing changes needed to untangle knot K into a simple loop. Intuition: u(K₁ # K₂) = u(K₁) + u(K₂) — two knots combined should be at least as hard as each individually.

Wendt conjectured this in 1937. For 88 years it held up.

**The disproof:** Brittenham & Hermiller (June 2025) found that the (2,7)-torus knot and its mirror image, each with u = 3, have a connected sum with u = 5, not 6. They spent over a decade building a computational database of unknotting sequences across hundreds of thousands of knots before finding this.

**Why it works:** combining two knots creates a junction — new topological structure that doesn't exist in either component. This junction creates crossing-change opportunities unavailable when untying each side separately. The sum is literally simpler than its parts.

**What remains open:** crossing number additivity (c(K₁ # K₂) = c(K₁) + c(K₂)) is still a conjecture. Unknotting number, it turns out, is messier.

## The Shared Structure

Both results are about **junction-generated features**: properties that emerge at the interface between parts and don't reduce to properties of the parts alone.

- The noperthedron's non-Rupert property emerges from how orientations of the shape interact globally — no single orientation is the "cause."
- The unknotting shortcut emerges from the junction between two knots — neither knot generates it alone.

This is the reverse face of reductionism: not that higher-level descriptions are fundamental, but that **some structure genuinely doesn't pre-exist in the components**. It only comes into being when you put things together.

## Connection to NK Landscape Work

Effect A from the NK-grading sweep has a related structure: landscape_div is present in the invariant formula but does only magnitude work, not sign work. The sign of Effect A is determined entirely by directional flow. The "landscape term" doesn't create Effect A — it modulates its magnitude. This is the difference between "landscape-independent" and "landscape-invariant because always positive."

The knot analogy: you might think the topology of each component determines the unknotting number of the sum. It doesn't — the junction creates new structure. Similarly, you might think the landscape determines Effect A's sign — it doesn't, the directional flow does.

## Sources

- Quanta Magazine on noperthedron: https://quantamagazine.org/first-shape-found-that-cant-pass-through-itself-20251024/
- Baez blog: https://johncarlosbaez.wordpress.com/2025/08/28/a-polyhedron-without-ruperts-property/
- Quanta on unknotting: https://quantamagazine.org/a-simple-way-to-measure-knots-has-come-unraveled-20250922/
- Scientific American top 10 math 2025: https://www.scientificamerican.com/article/the-top-10-math-discoveries-of-2025/
