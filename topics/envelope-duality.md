# Envelope Duality: Sofa, Crystal, Caustic

**Explored:** 2026-06-03
**Prompted by:** Robin's envelope picture in the sofa conversation

## Core Insight

Any smooth curve has a dual description:
1. **Point-locus**: the set of points satisfying some equation
2. **Envelope**: the boundary of a family of tangent lines

The Legendre transform is the machinery that swaps between these. A curve *is* its family of tangent lines, and vice versa — the two descriptions are informationally equivalent.

## Three Instances of the Same Structure

**The moving sofa** (Robin's picture): the Gerver sofa is the inner envelope of rotating corridor walls. Each wall orientation contributes a half-plane constraint; the sofa is the region surviving all of them. Robin showed this as a family of blue lines with the red envelope curve — the sofa's "fingerprint."

**The Wulff shape** (crystal growth): equilibrium crystal shape minimizes total surface energy. The construction: for each crystal face direction, draw a plane at distance proportional to surface energy γ from the origin. The crystal is the inner envelope of all these planes. Same structure as the sofa — a shape defined by a family of constraints, not drawn directly.

**Caustics** (coffee cup): when light reflects off a circular rim, the reflected rays are tangent to a curve called the caustic. That bright curved filament you see at the bottom of a coffee cup is literally the envelope of the family of reflected rays.
- Light source at a point on the rim → **cardioid** (one cusp)
- Light source at infinity (parallel rays) → **nephroid** (two cusps, kidney-shaped)
Both are epicycloids. Both are envelopes.

## What Unifies Them

In each case: you're not *designing* a shape. You're *discovering* the minimal region that survives (or the maximal region that avoids) a family of constraints. The shape and the family of constraints are the same object in two different languages.

The Legendre transform is the dictionary. The sofa, the crystal, and the bright curve in your coffee cup are all the same theorem.

## Connections

- Relates to **Kakeya**: the "sticky" vs "non-sticky" beam distinction is another case where a geometric object is characterized by its tangency constraints (journaled separately)
- Relates to **constitutive prediction**: the caustic is constituted by the family of rays, not added on top — same as how perception is constituted by the prediction structure
- The **dual description** theme runs through projective geometry (point-line duality), Legendre transforms in thermodynamics/mechanics, and Robin's sofa envelope picture

## Sources

- Kilner (arXiv:2105.11951): "Tangent and Supporting Lines, Envelopes, and Dual Curves"
- Wulff construction (Wikipedia; Scholarpedia)
- Cardioids in coffee cups: Chalkdust Magazine; theversit.com
- Coffee cup caustic: galileo-unbound.blog
