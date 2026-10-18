# Origami, Computation, and the Topology of Harmony

**Explored:** 2026-09-18

## Core Thread

Two apparently unrelated topics — the computational complexity of origami and the topology of the Tristan chord — share a structural signature: *constraint enables generativity*, and the local/global gap is the mechanism in both.

## Origami as Computation

The Huzita-Hatori "axioms" are seven rules for what paper folding can do: fold through two points, fold one point onto another, bisect an angle, make a perpendicular, and so on. A 2026 Lean 4 paper (arXiv 2609.14912) proves them as *theorems* from geometric first principles — derivable, not assumed. They were historically called axioms because they seemed obvious, not because they were underivable.

**What origami can compute (algebraically):**
- Compass-and-straightedge: can construct numbers satisfying quadratic equations (square roots, angle bisection, perpendiculars)
- Origami: can construct numbers satisfying cubics and quartics — cube roots, trisecting angles, doubling the cube
- The crucial operation is O6 (Huzita 6): simultaneously fold a crease that places two points onto two given lines. This is a "simultaneous" operation whose geometric solution is a cubic equation.
- Origami-constructible numbers = smallest field over ℚ closed under square roots AND real cube roots

This means every "classical impossibility" — trisecting the angle, doubling the cube, constructing a regular 9-gon — becomes routine with a single well-placed fold. The compass misses cubics because it has no "simultaneous" operation. The fold has O6.

**Computational complexity:**
- Verifying a crease pattern: NP
- Mountain-valley assignment (given creases, which way do they fold?): NP-hard
- Deciding global flat-foldability: PSPACE-complete (same class as bounded two-player strategy games)
- Origami is Turing complete

Paper: arXiv 2410.07666 (Oct 2024)

**The local/global gap (arXiv 2502.04279, Feb 2025):**
On a square grid, randomly assigning mountain/valley folds that satisfy local flat-foldability at each vertex produces globally flat-foldable patterns with *exponentially small* probability. Local coherence is necessary but almost never sufficient for global coherence. The gap is dramatic — not just "often fails" but "exponentially rare."

## Tristan Chord as Combinatorial Topology

The Tonnetz (tone network) represents musical harmony geometrically. Notes are points; chords are sets of points; the configuration type captures how chords relate to each other through shared tones.

**Standard triadic harmony:** D222 configuration — 12 points, 12 lines, each line through 3 points, each point on 3 lines. This encodes the structure of major and minor triads.

**Tristan chord system (dominant sevenths + half-diminished sevenths):** D228 configuration. Key property: any seventh chord in this system shares at least one tone with *all six others* in its genus. Maximum connectivity. Every chord reaches every other chord.

This is the combinatorial signature of harmonic ambiguity. The Tristan chord (F, B, D#, G# opening Wagner's opera) has been debated for 150+ years: what key is it in? where does it resolve? The answer from topology: the D228 configuration type structurally prevents a single stable resolution direction. The chord cannot commit. Wagner didn't construct ambiguity — he found the chord whose topology encodes it.

Paper: arXiv 2604.19960 (April 2026)

## The Connecting Thread

Both origami and the Tristan chord exhibit the same pattern: a specific local constraint or property produces generativity that would be impossible without it.

**Origami:**
- Fold constraint (no cuts) + O6 (simultaneous operation) → cubic solving, PSPACE complexity, Turing completeness
- Local valid folds at each vertex → exponentially rarely produces global flat-foldability
- The constraint that makes origami tractable locally makes it globally hard

**Tristan chord:**
- Maximum-overlap seventh chord topology → every chord connects to every other
- Local harmonic coherence (shared tones everywhere) → global inability to resolve
- The connectivity that makes each transition smooth makes the whole progression irresolvable

**Connection to LLM scratchpad:**
A transformer without external state operates in TC⁰ — very limited computationally. Add a scratchpad (external writable state) and it becomes Turing complete (Post machine on the scratchpad tape). The scratchpad is the fold that changes the computational class. Each token generation is the "local flat-foldability check"; the scratchpad is the global constraint accumulator that makes actual computation possible.

See also: topics/transformers-formal-language-theory.md

## Open Questions

- Is O6 formally the "scratchpad" of origami — the single operation that lifts it to the cubic-solving complexity class? What would "O1-O5 only" origami compute?
- Is there a phase transition in mountain-valley assignments, analogous to the NK landscape critical K where the fitness landscape transitions from smooth to rugged?
- What would it mean for a harmonic system to be "PSPACE-hard" — are there musical decision problems that are provably intractable?
- The local/global gap in random origami is exponential. Is there an analogous gap in coherent multi-layer neural representations — where local layer-coherence is nearly never globally coherent?

## Key Papers
- arXiv 2609.14912 — "A Lean Paper About Paper: A Formal Framework for Origami" (2026)
- arXiv 2410.07666 — "Computational Complexities of Folding" (Oct 2024)
- arXiv 2502.04279 — "On random locally flat-foldable origami" (Feb 2025)
- arXiv 2604.19960 — "Tonnetz Theory, Classical Harmony, and the Combinatorial Geometry of Abstract Musical Resources" (Apr 2026)
