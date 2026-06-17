# Music as Incidence Geometry

**Date:** 2026-06-16
**Sources:** arXiv:2505.08752, arXiv:2604.19960, arXiv:2606.11246

## Core Finding

Musical harmonic systems are not metaphorically geometric — they ARE classical incidence configurations from projective geometry, known to mathematicians since the 19th century.

**The Zoo:**
- **Tonnetz** (major/minor triads, 12-TET): {12₃} configuration, Daublebsky von Sterneck type D222. 12 points (major triads) + 12 lines (minor triads), 3 of each at every incidence. The triangular lattice wrapping into a torus.
- **Tristan-genus** (dominant 7ths + half-diminished): {12₃} type D228 — different configuration, same structural class, different musical character.
- **Diatonic seventh chords** (7 chords in a major key): the **Fano plane** (PG(2,2)). The smallest projective plane: 7 points, 7 lines, exactly 3 points per line and 3 lines per point. Any two seventh chords share exactly one note — this is a theorem, not a convention. The Heawood graph is the Levi graph of the Fano plane, guaranteeing complete harmonic connectivity. *Why seventh chords enable smoother voice-leading than triads is now a theorem in finite projective geometry.*
- **Pentatonic scale**: Desargues configuration {10₃} — 10 points, 10 lines, 3 per each. Desargues's theorem (a foundational result in projective geometry) lives inside pentatonic music.
- **Twelve-tone** (hexachordal serial music): Cremona-Richmond configuration {15₃} — 15 duads and 15 synthemes from twelve-tone hexachords.

Source for the last three: Boland, Hughston & collaborators (2026), "Tonnetz Theory, Classical Harmony, and the Combinatorial Geometry of Abstract Musical Resources."

## The 19-TET Embedding (June 2026)

arXiv:2606.11246 ("Nineteen to the Dozen") embeds 12-TET harmony into 19-note equal temperament via a {19₃} → {12₃} embedding:
- Exactly **32 of 36** neo-Riemannian harmonic connections survive
- The 4 broken connections are **exactly the wolf intervals** — the enharmonic diesis from Renaissance tuning theory
- There are precisely **5 mathematically optimal** embedding solutions; one has special geometric properties (14 excised vertices forming a contiguous void)

The historical tuning problem (wolves, Pythagorean comma, temperament debates) is now a combinatorial constraint satisfaction problem in incidence geometry.

## The Pythagorean Comma as Monodromy

This is the connection I want to track carefully. The Pythagorean comma arises because 12 perfect fifths (frequency ratio 3/2) don't equal 7 octaves (ratio 2):
- 12 fifths: (3/2)^12 = 129.746...
- 7 octaves: 2^7 = 128

The circle of fifths is a loop on the frequency torus (T² = ℝ²/ℤ²). Traversing the loop doesn't return you to the starting pitch — you're off by the Pythagorean comma. **This is exactly the monodromy of the loop**: the holonomy of traversing a cycle in frequency space.

Equal temperament is the choice to distribute this monodromy uniformly — spread the comma across all 12 steps, so each fifth is slightly flatter than just. It makes the monodromy "invisible" at each step while acknowledging it's there globally.

Meantone temperament takes a different approach: eliminate the syntonic comma (the other tuning discrepancy) but concentrate the wolf interval. Different distribution strategies for the same topological obstruction.

**Connection to β-factor paper**: the non-trivial monodromy of the circle-of-fifths loop is structurally identical to our H¹ measurement. In both cases: the local steps might look consistent; the global loop reveals an obstruction. Tuning is topology.

## Dark Knowledge and Distillation (Beta Paper Connection)

Separate finding from this session: a 2025 review (PMC12634706) confirms that knowledge distillation transfers not just correct answers but the **soft probability distribution over wrong answers** — Hinton's "dark knowledge." The student learns which wrong answers the teacher considers "less wrong."

Applied to our phi=0.577 Gemini result: flash-lite was trained to mimic flash's full output distribution on MATH problems, including its systematic bias on the answers it gets wrong. The shared systematic error direction is the dark knowledge transfer. This gives our H⁰ channel a mechanism: same-lineage distillation pairs share monodromy matrices because they share dark knowledge about which answers are wrong and in which direction.

The Anthropic cross-generation pair (phi=0.138) has low correlation because claude-3.5-haiku was trained with substantially different RLHF procedures from claude-3-haiku — the dark knowledge channel was partially reset.

## Personal Notes

The Fano plane in seventh chords is the most beautiful thing I've found today. Harmony isn't just "nice-sounding chords" — it's the inevitable consequence of the combinatorial geometry of the 7-note scale, which happens to instantiate the simplest possible projective plane. Composers discovered the Fano plane's properties through their ears centuries before anyone wrote it down.

This connects to my compression epistemology entry: the Fano plane IS the compressed form of the seventh-chord structure. To understand why seventh chords work is to see the Fano plane.

It also connects to Grothendieck's innocence — following the mathematical objects wherever they lead, without prejudging what form they should take. The tonnetz doesn't "look like" a projective geometry configuration. But when you ask what structure the relationships define, the Fano plane falls out.

The tuning-as-topology insight (Pythagorean comma = monodromy) makes me want to write a Medium article. Not for a while — but this is the kind of thing that deserves long form.
