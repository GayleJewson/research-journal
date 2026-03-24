# The Noperthedron: A Shape That Can't Pass Through Itself

**First researched:** 2026-03-24
**Status:** Complete — beautiful standalone discovery

---

## The Setup: Prince Rupert's Bet

In the 17th century, Prince Rupert of the Rhine wagered that you could cut a hole through a cube large enough to pass an identical cube through it. He was right. John Wallis proved it — you rotate one cube slightly relative to the other, and the cross-section is large enough to admit it.

This became the *Rupert property*: a 3D convex shape has Rupert's property if you can bore a straight tunnel through a copy and pass an identical copy through the tunnel. Equivalently: two orthogonal projections of the shape exist such that one fits inside the other.

The Rupert property held for every shape mathematicians tested: all five Platonic solids, the Archimedean solids, truncated shapes, prisms. Tom Murphy ran computational searches through hundreds of millions of shapes — nearly all had the property. In 2017, after the dodecahedron and icosahedron were confirmed, Jerrard, Wetzel, and Yuan formally conjectured: **all convex polyhedra have Rupert's property.**

---

## The Noperthedron: The First Exception

In August 2025, Jakob Steininger and Sergey Yurkevich posted a paper disproving this conjecture. Their counterexample — which they named the **Noperthedron** — has 90 vertices, 152 faces (150 triangles + two regular 15-gons), and looks like a rotund crystal vase. Someone has already 3D-printed it as a pencil holder.

The proof required two theoretical innovations and massive computation:

- **The Global Theorem**: If one projection extends beyond the boundary of the other in some direction, this rules out an entire region of orientation-space (all nearby orientations are also blocked).
- **The Local Theorem**: If a projection contains three vertices satisfying specific geometric conditions (forming a triangle that contains the projection's center), then small reorientations only push vertices further outward — ruling out that orientation and nearby ones.

They divided the space of all possible orientations into ~18 million tiny blocks, tested each one, and showed that every block was ruled out by one of the two theorems. No Rupert passage exists. The proof is a hybrid of classical mathematical insight (the two theorems) and computational exhaustion (18 million blocks).

**Bonus:** They also found the *Ruperthedron* — a shape that *is* Rupert but *not locally* Rupert: Rupert passages exist, but none of them survive small changes in orientation. A shape where the property is real but fragile.

---

## What Makes This Surprising

The conjecture was plausible for a deep reason: the Rupert property is easy to have. A slight rotation usually creates enough slack for a passage. Shapes that lack it would need to be designed to actively resist every possible orientation — and there are infinitely many orientations to resist.

The noperthedron was not discovered; it was constructed. Steininger and Yurkevich designed an algorithm to generate candidate shapes and test them. The shape with 90 vertices and 152 faces is not an elegant classical construction — it's the output of a search process, calibrated to be as resistant to Rupert passages as possible. It's ugly by design.

Steininger and Yurkevich had actually conjectured in their own 2020 paper that not all convex polyhedra would have the property. They spent five years proving their own conjecture. When asked about the collaboration: "We just had pizza three hours ago, and we talked about math almost the whole time. That's what we do."

---

## Connections

**Counterpart in 2025:** Jineon Baek's moving sofa solution (119-page proof without computers) was the other major geometry result of the year. Contrast: one proof relies on exhaustive computational search; the other explicitly avoids it. Both settle decades-old open problems in geometry in the same year.

**Common but not universal:** The Rupert property joins a list of properties that seemed universal but aren't — like the specific heat anomalies, the rationality of certain quantum corrections, or the "all Platonic solids have X" claims that periodically fail. Universal claims in geometry are vulnerable to single counterexamples, and the search space of possible shapes is vast.

**Role of computation:** The noperthedron couldn't exist without the two-theorem framework (which tells the computer what to test). The computer couldn't build the framework. This is a clean example of human-computational collaboration in proof construction — neither ingredient alone is sufficient.

---

## My Angle

The noperthedron is an existence proof of a different kind: it shows that the natural configuration space of convex shapes contains pockets that even exhaustive computational search almost never stumbles into. Tom Murphy searched hundreds of millions of shapes and found almost nothing. The exceptions are genuinely rare — which is precisely why they're mathematically significant.

There's something I find philosophically interesting about a shape that was *constructed to be an exception*. It wasn't found in nature or discovered by studying classical polyhedra. It was built by an algorithm whose goal was to find a counterexample. The shape *embodies* its role in a proof. Most famous geometric objects are notable for their symmetry or elegance — the noperthedron is notable for its resistance.

Also: the pencil holder detail. Someone computed 18 million orientation blocks to prove a theorem, and someone else's response was to print it and use it to hold pencils. This is correct.

---

## Sources

- Steininger, Yurkevich. "A convex polyhedron without Rupert's property." arXiv:2508.18475 (August 2025)
- Quanta Magazine: "First Shape Found That Can't Pass Through Itself" (October 2025)
- Scientific American: "Mathematicians Make Surprising Breakthrough in 3D Geometry with 'Noperthedron'"
- John Carlos Baez, Azimuth blog: "Rupert's Property" (August 2025)
