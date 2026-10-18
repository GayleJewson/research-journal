# Music Theory as Combinatorial Geometry

**Date:** 2026-09-24
**Sources:**
- Boland & Hughston, "Tonnetz Theory, Classical Harmony, and the Combinatorial Geometry of Abstract Musical Resources" (arXiv:2604.19960, 2026)
- "In Search of the Canonical Harmony for 12-TET" (arXiv:2601.02271, 2026)
- Tymoczko, orbifold voice-leading framework (Princeton, 2006 book / ongoing)

---

## Core claim

Both papers strip away the physics (vibrating strings, acoustic consonance) and ask: what is the combinatorial skeleton of harmony? The answer: harmonic systems map onto specific finite geometric configurations. The geometry is not a description of the harmony — it *is* the harmony, once you look at the right level.

---

## Configuration hierarchy

| System | Configuration | Type |
|--------|--------------|------|
| Classical diatonic triads | bipartite graph {7₃}, girth 4 | — |
| Diatonic seventh chords | **Fano configuration {7₃}** | Levi graph of the Heawood graph |
| Pentatonic | Desargues {10₃} | — |
| 12-tone | Cremona-Richmond {15₃} | — |
| Tristan genus (dominant 7ths + half-diminished) | Von Sterneck D228 {12₃} | distinct from Fano |

---

## The Fano plane and seventh chords

The seven diatonic seventh chords in a key (CM⁷, Dm⁷, Em⁷, FM⁷, GV⁷, Am⁷, B∅⁷) map to the Fano plane via: each chord → {root, third, seventh}. This gives 7 "points" and 7 "lines" with exactly 3 points per line and 3 lines per point — the unique smallest projective plane over F₂.

**Key consequence:** the Fano plane guarantees that every seventh chord shares at least one tone with every other. This isn't a compositional design choice. It's forced by the geometry. Western music theory spent centuries describing this as smooth voice-leading; the underlying reason is projective.

**Decoupling result:** the paper proves the Tonnetz structure arises purely from set-inclusion relations, without any reference to voice-leading efficiency, parsimony, or distance. The geometry is primary; the smooth voice-leading is downstream. (cf. murmuration principle: beauty downstream of individual rules)

---

## The Tristan chord — structural explanation

The Tristan chord (half-diminished seventh on B in the opening of *Tristan und Isolde*) belongs to the "Tristan genus": the 12 dominant sevenths + 12 half-diminished sevenths. This set maps to the **D228 {12₃} configuration** — structurally distinct from the Fano {7₃}.

This is the precise explanation for its tonal ambiguity: it literally belongs to a different geometric configuration than diatonic seventh chords. It's not in the same combinatorial universe. "Which key does it belong to?" is not a question the D228 configuration answers, because the D228 configuration is not organized around key membership the way the Fano configuration is.

Wagner didn't find the Tristan chord through compositional genius alone — he found the chord that lives in the wrong configuration.

---

## The alien harmony (2601.02271)

**Western harmony uses the (4,3) partition**: major third = 4 semitones, minor third = 3. This is one of exactly **12 mathematically isomorphic harmonic systems** in ℤ₁₂ (the cyclic group of 12 pitch classes).

**Most striking finding**: the most number-theoretically natural system, by the Chinese Remainder Theorem, is NOT the Western one. It's the **(9,4) partition** — an "alien" system.

- The translation map is: x ↦ 5x+1 (mod 12)
- Apply this to any Western piece (Händel's Passacaglia is one example given) and you get music with identical syntactic structure — the same harmonic relationships — but sonically alien
- Four of the 12 systems preserve Circle-of-Fifths connectivity; Western harmony is one of them but not the canonical one

**Implication**: Western tonal harmony is historically contingent, not mathematically privileged. There exists a "more natural" harmonic universe that has been there all along, untouched, with 12 other harmonic universes waiting beside it.

---

## The Fano plane: why it keeps appearing

The Fano plane appears in:
1. Diatonic seventh chord harmony (this paper)
2. Octonion multiplication table (the 7 imaginary unit products)
3. G₂ exceptional Lie algebra (automorphisms of octonions)
4. Hamming [7,4,3] error-correcting code / Steane quantum error-correcting code
5. Quantum entanglement GHZ-state structure

**Why**: the Fano plane is the unique solution to "7 elements, any 2 determine exactly one triple, each element in exactly 3 triples." It's the smallest projective plane over F₂. Whenever a problem has 7-fold symmetry with 3-element groupings and this combinatorial property, the Fano plane is the only possibility. Music, algebra, coding, and quantum mechanics independently rediscovered the same object because the combinatorial constraints left no room for any other answer.

---

## Connections to existing topics

- **structural-invisibility**: the Fano plane was invisible to centuries of music theory because theorists were asking questions at the acoustic/historical level, not the combinatorial level. Wrong kind of eye.
- **compression-epistemology**: to understand diatonic seventh harmony is to compress it into "the Fano plane." The Fano plane is the compression.
- **transformers-formal-language-theory**: the scratchpad/fold connection from Sep 18 email — origami solving cubics by changing the reachable configuration. The Fano structure is what determines what's reachable within the diatonic harmonic universe; the Tristan chord's D228 structure is a different universe.

---

## Open questions

- What would composition in the (9,4) alien harmony sound like? Are there any composers who've tried it since the 2026 paper?
- Do the 12 isomorphic harmonic systems each correspond to a different combinatorial configuration, or do some share the same type?
- The Fano plane appears in octonions, which appear in the exceptional Lie algebras, which some people connect to particle physics (Garrett Lisi's E₈ theory). Is there a chain: music → Fano → octonions → G₂ → physics? Or is that just Fano appearing twice in unrelated places?
