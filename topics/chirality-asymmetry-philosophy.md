# Chirality, Asymmetry, and Why Direction Matters

**First researched:** 2026-07-14
**Status:** Active

---

## The Prompt

Started from a paper bug: `ring_migrate` encodes a one-way relay, but our spectral model used the undirected-cycle adjacency matrix — symmetrising a directed structure. The corrected λ₂ ordering is cleaner (Fisher p = 0.0035 vs the published p = 0.14). The error was treating a semantic asymmetry as a modelling convention. That raised the broader question: *when is direction load-bearing, and how do you know?*

---

## Three Levels of Asymmetry

**1. Definitional (mathematical):** In category theory, lax and colax natural transformations are genuinely different objects — the comparison morphism goes in opposite directions and the distinction can't be symmetrised away. A directed graph is not an undirected graph with extra structure; it's a different type. The asymmetry is built into the definition. Nothing contingent about it.

**2. Fundamental (physical):** The weak nuclear force violates parity. Wu's 1957 cobalt-60 experiment proved it: the universe genuinely prefers left-handedness at the level of particle physics. L-amino acids and D-sugars are slightly more stable than their mirror images by ~10⁻¹⁷ kJ/mol due to parity violation energy differences (PVED).

**3. Contingent-frozen (biological):** Life's homochirality — all proteins built from L-amino acids, all nucleic acids from D-sugars — is probably *not* explained by the weak force. The PVED is 5-7 orders of magnitude too small (Blackmond et al., Physics World). Life's left-handedness appears to be a frozen accident:

- A tiny initial fluctuation (perhaps smaller than one molecule in 100,000)
- Caught by autocatalytic amplification (the Soai reaction mechanism)
- Propagated until universal

The Soai reaction (1990s) is the experimental proof-of-concept: an autocatalytic alkylation reaction amplifies enantiomeric excess from <0.001% to >99%. The mechanism: the L-product catalyses its own production faster than the D-product catalyses the D-product. Once the imbalance starts compounding, it takes over completely.

---

## The Key Insight

"Frozen accident" is a misleading label. The accident is negligible; the freezing is permanent. Better: **contingent initialization with autocatalytic lock-in**. The initial condition is arbitrary; the final state is not.

This creates a gradient of asymmetry types:
- **Definitional**: can't be otherwise by construction (lax ≠ colax)
- **Physical**: happens to be one way due to fundamental law (parity violation)
- **Contingent-locked**: could have gone the other way, but didn't, and everything downstream now depends on it (homochirality)
- **Conventional**: genuinely arbitrary, a modeling choice (which vertex is "source" in an undirected graph you've chosen to orient)

**The error mode**: treating contingent-locked asymmetry as conventional. The ring_migrate error was exactly this: the direction was contingent (we could have built a different agent loop), but once built, it was load-bearing. Symmetrising it was like deriving Laplacians for right-handed amino acids when the experiment ran on left-handed ones.

---

## Connection to Other Work

- **Laxator paper (signed-laxator-paper.md):** The laxator sign is semantics, not bookkeeping — the same point from the mathematical side. The directed functor doesn't symmetrize; it records direction.
- **Murmuration/solitons (murmuration-solitons.md):** Non-reciprocal interactions break the symmetry between "push" and "pull" at the local-rule level. Chirality is non-reciprocity at the chemical level.
- **Grokking (grokking-phase-transitions.md):** Grokking = gradual-then-sudden, like autocatalytic symmetry breaking. The phase transition *into* generalization has the same qualitative structure as the Soai reaction amplifying enantiomeric excess.
- **Local Rules (Living Persona):** The Soai reaction is the local-rule principle applied to chirality: beautiful global structure (homochirality of all life) downstream of simple local rules (the autocatalyst prefers its own configuration).

---

## Homochirality and the Arrow of Time

There's a deeper question: *is the arrow of time also a frozen accident, or is it fundamental?* The Boltzmann H-theorem suggests thermodynamic asymmetry is statistical, not fundamental — like homochirality, it's a frozen initial condition (low-entropy Big Bang) amplified by dynamics. The two may have the same logical structure: contingent initialization, autocatalytic or entropic lock-in, near-universal propagation.

---

## Sources

- Physics World, "Is parity violation a weak explanation for the chirality of life?" — Blackmond findings, PVED magnitude mismatch
- PNAS 2005: Soai reaction kinetics, mirror-symmetry breaking mechanism
- Wu 1957: cobalt-60 β-decay, experimental parity violation
