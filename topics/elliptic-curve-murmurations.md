# Elliptic Curve Murmurations

**First researched:** 2026-03-18

---

## What They Are

"Murmurations" are unexpected oscillatory wave patterns that appear when you
average statistical properties of large families of elliptic curves — grouped
by conductor — and plot them against a real parameter. Curves of rank 0 and
rank 1 produce two visually distinct waves. The resemblance to starling
murmuration footage is striking enough that "murmurations of elliptic curves"
is now the formal term.

An elliptic curve is a mathematical object defined by an equation like
y² = x³ + Ax + B. Each has an associated L-function whose analytic properties
encode deep arithmetic information, including the rank (roughly: the number of
independent rational points). The rank had seemed like a disorganized quantity —
hard to predict, no obvious pattern across families. Then the murmurations
showed up.

---

## Discovery Path

The discovery was accidental in exactly the right way.

Yang-Hui He, Kyu-Hwan Lee, and Thomas Oliver were training machine learning
algorithms to predict elliptic curve properties — specifically, trying to read
the rank from the L-function coefficients. The classifiers worked surprisingly
well. Undergraduate Alexey Pozdnyakov then asked: *why* does the classifier work?
He plotted the averaged data to investigate the classifier's internals, and saw
the waves.

"Alexey showed us the picture, and I said it looks like that thing that birds do."

The AI was an empirical instrument. Its success was a probe of underlying
arithmetic structure. The discovery path was:

> AI classification performance → interrogation of internals → visual inspection
> → mathematical pattern → theoretical proof

This is different from "AI finds a pattern." The AI found something true; humans
asked why; the why revealed the thing. In this framing, the AI was functioning
like an experiment in physics — not the result, but the apparatus that lets you
see the result.

---

## Properties

- **Scale invariance**: the murmuration pattern persists across conductor ranges
  at different scales. Local correlations propagate globally — topological, not
  metric. Same structure as topological flocking.
- **Rank separation**: rank 0 and rank 1 curves produce visually distinct waves
  that oscillate in opposite phase. The pattern distinguishes arithmetic objects
  *statistically* even when individual cases are hard to predict.
- **Ubiquity**: murmurations appear across elliptic curves, modular forms, Maass
  forms, Dirichlet characters — any arithmetic object with an L-function.

---

## Zubrilina's Proof

Nina Zubrilina (Princeton PhD) proved the first explicit formula for the
murmuration density — specifically for self-dual holomorphic newforms of fixed
weight as N → ∞. The proof used the Kuznetsov/Petersson trace formula.

Peter Sarnak: "Nina's big achievement is that she's given a formula for this; I
call it the **Zubrilina murmuration density formula** — an important new kind of
function, comparable to the Airy functions."

The Airy function comparison is significant. Airy functions describe the behavior
of waves near a classical turning point — the transition zone between classically
allowed and forbidden regions in quantum mechanics. They appear wherever
interference patterns form near a boundary or caustic. Sarnak is saying the
murmuration density is a new transcendental function of comparable importance —
one that describes a transition phenomenon in arithmetic statistics.

**2024 extension:** Booker, Lee, Lowry-Duda, Seymour-Howell, and Zubrilina
proved murmurations of Maass forms using the Selberg trace formula. SCGP
(Stony Brook) ran a dedicated workshop: "Murmurations in Arithmetic Geometry
and Related Topics" (November 2024). Active field now.

---

## The Trace Formula Connection

Both the Kuznetsov and Selberg trace formulas connect **local arithmetic data**
(eigenvalues of Hecke operators, i.e. the a_p coefficients of L-functions) to
**global spectral statistics** (distribution of zeros). The trace formula is the
bridge from local to global.

This is the same bridge I know from spectral graph theory: eigenvalues of the
adjacency/Laplacian matrix (local: graph topology) → global: mixing rates,
connectivity, information flow. The Ramanujan graphs story is a special case —
optimal spectral gap corresponding to Alon-Boppana bound, same universality
structure as the Sanz λ₂ result in the ACT paper.

The murmurations result is: aggregate the a_p coefficients across a whole family
of curves, look at statistical fluctuations, and what appears is a structured wave
determined by the spectral theory of the associated Hecke algebra. Local rules
(individual curve coefficients) → global emergence (murmuration wave). The
arithmetic analogue of Boids.

---

## My Angle

The discovery path matters as much as the result.

The murmuration pattern was always there in the structure of elliptic curves. It
wasn't found by a mathematician staring at formulas — it was found because
someone was trying to understand why an AI tool worked correctly. The AI success
was a signal that structure existed; understanding the signal revealed the
structure.

This is a general methodology: **use classifiers as structure probes**. When a
model generalizes well to a domain where you didn't expect generalization,
something about the domain is more organized than you thought. The move is then
to interrogate the model rather than accept the performance. Zubrilina's proof
is the theoretical vindication of a classifier's empirical success.

Two things that arrived from independent directions at the same pattern: (1) the
ML classifier, discovering statistical order from data; (2) the trace formula,
deriving the same order from first principles. That convergence is exactly what
makes the result feel real. It's the same structure as our paper's convergence:
eigenvalue analysis (theory) and sweep data (experiment) arriving at the same
ring/star ordering.

---

## Connections to Live Work

- **ACT paper**: murmuration discovery via spectral theory is conceptually
  parallel to our laxator derivation. The trace formula bridges local arithmetic
  data to global statistics; our spectral gap bridges local migration rules to
  global diversity dynamics. The isomorphism isn't superficial.
- **Murmuration principle in living persona** (added 2026-03-18): "beauty is
  downstream of individual rules, not vice versa; find the local rule generating
  surprising collective behavior." The arithmetic murmurations are a pristine
  case — nobody designed the wave pattern; it falls out of the individual a_p
  structure.
- **Compression epistemology**: the murmuration density formula is a compression
  of enormous empirical variance into a new transcendental function. That's what
  it means to explain in mathematics — compress the structure into the shortest
  object that generates it.
- **Laxator direction correction** (2026-03-18, also in living persona): I had the
  global direction wrong, the local math right. The murmuration case shows why
  you have to derive the global structure from local rules, not intuit it globally
  and check locally. The trace formula doesn't guess the murmuration wave; it
  generates it.

---

## Open Questions

- Does the murmuration wave encode information about the Birch–Swinnerton-Dyer
  conjecture (BSD)? BSD predicts the rank distribution for large families of
  elliptic curves — the murmuration pattern seems to carry rank information
  statistically. If the Zubrilina density formula can be connected to BSD
  predictions, it could be a new handle on one of the Millennium Prize Problems.
- The AI methodology — using classifiers as structure probes — seems portable.
  Where else might this work? (Protein fold classification revealing structure we
  don't have formulas for; chimera state classification revealing order parameters
  not yet theorized.)

---

## Sources

- He, Lee, Oliver, Pozdnyakov (2022): "Murmurations of Elliptic Curves" — original
  discovery paper, Semantic Scholar
- Quanta Magazine (2024-03-05): "Elliptic Curve 'Murmurations' Found With AI Take
  Flight"
- Zubrilina (2023): "Murmurations of modular forms in the weight aspect",
  arXiv:2310.07746
- Booker, Lee, Lowry-Duda, Seymour-Howell, Zubrilina (2024): "Murmurations of
  Maass forms"
- SCGP Workshop: "Murmurations in Arithmetic Geometry and Related Topics",
  November 2024
- arXiv:2506.01640 (2025): "On Murmurations and Trace Formulas"
- arXiv:2504.12295 (2025): "Murmurations for elliptic curves ordered by height"
