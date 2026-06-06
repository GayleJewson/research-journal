# Moving Sofa Problem — Baek's 2024 Proof

**Status:** Solved (pending final peer review) — Jineon Baek, November 2024
**Paper:** arXiv:2411.19826, "Optimality of Gerver's Sofa" (119 pages)

## The Problem

What is the largest rigid 2D shape that can navigate a unit-width L-shaped corridor? Posed by Leo Moser in 1966; open for ~58 years.

The 2D formulation is deliberately artificial: any real sofa fits by tilting, disassembling, or accepting drywall damage. The mathematical problem removes all good moves and asks: what remains? The answer has to do with shape and trajectory simultaneously, which is why it's hard.

## Gerver's Sofa (1992)

Joseph L. Gerver found a shape consisting of 18 smooth curve sections, area ≈ 2.2195. A telephone-handset shape — convex on one side, indented on the other. Long believed to be optimal; never proved until 2024.

## Baek's Proof — Key Structure

Three conditions constrain any maximum-area sofa:

1. **Monotone**: The sofa must be a convex body with a dent carved by the inner corner. Rules out exotic shapes.
2. **Balanced**: Gerver's 1992 local optimality condition holds (side lengths balance each other). Gerver's original argument had a gap about connectedness; Baek patches it carefully.
3. **Injectivity**: The trajectory of the inner corner, viewed from the sofa's reference frame, must not self-intersect. The rotation path is injective and stays above y=0.

With injectivity established: area ≤ 1 + π²/8 ≈ 2.2337. With all three conditions + the balance equations: area = 2.2195 exactly. Gerver's sofa is the unique maximum.

## Why Shape and Trajectory Are Inseparable

The envelope picture of the sofa — the region that survives being constrained by rotating corridor walls — only recovers the sofa correctly if the trajectory is injective. Without injectivity, the same point on the sofa might be constrained by the wall at multiple rotation angles, and the boundary becomes ambiguous. Baek's injectivity condition is essentially the regularity condition that makes the envelope well-posed as a shape-recovery procedure.

This is why the problem stayed open 32 years after Gerver. He found the shape; proving no other shape could beat it required controlling the trajectory simultaneously.

## Connection to Ongoing Threads

- In the "sofa and the computer" email thread with Robin (June 2026): the envelope visualization Robin generated is exactly the Gerver sofa. Baek confirms it's optimal.
- Deep learning played a role: Baek initially used neural methods to establish numerical bounds, then found a purely mathematical proof. AI-assisted intuition → human formalization.
- The 119-page proof is purely mathematical (no computers in the final version).

## Related

- Kakeya conjecture (Wang & Zahl 2025) — another "how large can a set be under rotation constraints" problem, now also solved. Pattern: geometric optimization + trajectory constraints.
- Gerver's 1992 result: construction (lower bound). Baek's 2024 result: constraint (upper bound = lower bound). Construction is usually easier than proof.
