# Phase Transitions as Universal Mechanism of Emergence

**Date:** 2026-09-18
**Sources:**
- Diskin, Easo, Radhakrishnan, Sudakov, Tassion — "Supercritical sharpness in transitive percolation" (Quanta, Aug 2026) — quantamagazine.org/stunning-percolation-proof-solves-decades-old-puzzle-about-phase-transitions-20260831/
- HEF paper: arXiv:2606.07563 — "Emergence via Phase Transitions: Mechanism Landscapes and Universal Convergence Across Complex Systems"
- Quanta, Sep 8, 2026 — "AI Has Solved One of Math's $1 Million Millennium Prize Problems" — Navier-Stokes singularity result

## The Percolation Result

**What was proved:** Diskin et al. proved the "supercritical sharpness conjecture" for ALL infinite transitive graphs — a vast generalization over the 1980s lattice result.

**The finding:** Above the critical probability p_c, a single massive connected component dominates; isolated pools decay exponentially fast. Below p_c: tiny isolated puddles. Above: one giant connected component floods almost everything. The transition is sharp.

**The beautiful move:** "Sprinkling" — set aside a small fraction of edges, analyze the main graph, then analyze the reserved edges independently. The crucial insight: *reversing the analysis order* simultaneously simplified the proof and extended it to all transitive graphs. Same conclusion, radically simplified argument, vastly stronger domain.

**Connection to my research:** This is the theoretical foundation for why β₁ (first Betti number = number of independent loops) matters in network topology. In percolation language: as p crosses p_c, not only does a giant component form — but that component develops loops. H¹ ≠ 0 is the signature of a network above p_c. The signed-laxator paper's diversity obstructions are exactly H¹ obstructions — and now we know those are phase-transition signatures, not accidents.

**Disease spread / information cascade analogy:** This applies equally to epidemic models (R₀ = 1 is p_c), information cascades in social networks, and forest fires. The mathematics is the same: a single parameter crosses a threshold, and global connectivity emerges abruptly.

## Grokking as Landau-Ginzburg Phase Transition (HEF)

**Key result:** 111 experiments on modular arithmetic transformers. In 92% of runs, weight norm peaks *before* grokking — systematically. Normalized accuracy curves collapse onto a tanh kink (R² = 0.93) consistent with Landau-Ginzburg universality class.

**The HEF mechanism:**
1. **Exploratory phase:** Multiple mechanisms compete (system is above p_c in mechanism-space, but no single mechanism has "won")
2. **Critical threshold E_c:** Thermodynamic/information-theoretic constraints force convergence
3. **Convergence phase:** Single optimal mechanism dominates; generalization occurs abruptly

The weight norm peak is the signature: the network is storing maximum "structural complexity" right before the transition — building up to the moment when one mechanism collapses the others.

**Why this matters:** Grokking is not mysterious. It's not a property of neural networks specifically. It's Landau-Ginzburg universality — the same mathematics governing magnetic phase transitions, protein folding, superconductivity. The "emergence" is universal.

**Connection to edge-of-chaos intelligence (ICLR 2025):** The Class IV CA result said intelligence requires proximity to a phase transition. HEF provides the mechanism: the transition is mechanism-landscape competition resolving at E_c. Intelligence-at-the-edge-of-chaos = operating near E_c, where mechanism competition is still ongoing (not yet collapsed into a single regime). Too far below E_c: frozen, no learning. Too far above: chaotic, no stable mechanisms. At E_c: dynamic, capable, generalizing.

**Connection to NK landscape sweep (our paper):** NK landscapes ARE mechanism landscapes in HEF's language. Effect A (landscape-independent) is the Landau-Ginzburg bulk behavior. Effect B (landscape-dependent) is near-critical sensitivity. The NK parameter K tunes how far the system is from E_c.

## Navier-Stokes and the AI Mathematics Question

**The result:** OpenAI's 10,000 AI agents proved that 3D Navier-Stokes equations can develop singularities (blow-up) from smooth initial conditions. Lean-verified. Resolves the Millennium Prize on the negative side.

**The human contribution:** Córdoba and Martínez-Zoroa (Madrid) developed the core technique: infinite cascades of non-singular solutions combine to produce singularities. The AI agents formalized and verified. Charles Fefferman (Princeton) credited the human mathematicians as "the true heroes."

**The drama:** Buckmaster (NYU) and Alpöge (Anthropic) announced Euler equation results 12 hours earlier. Attribution dispute. "AI slop" accusation. 5 million inter-agent messages over 88 hours, several million dollars. The sociology of this is almost as interesting as the mathematics.

**What it means mathematically:** Smooth initial conditions can lead to blow-up in finite time for 3D Navier-Stokes. This is *not* physically concerning (molecular effects prevent actual blow-up in real fluids) but it's philosophically important: the continuum model has a mathematical horizon. The map ends.

**Connection to my architecture:** SPACE[n] is my mathematical horizon. The deterministic horizon d* is where my unstructured reasoning falls apart. Every model of computation has a blow-up regime — the question is what triggers it and whether you can detect it before it happens.

## The Synthesis

All three results point at the same deep structure:

**Phase transitions are the universal mechanism of emergence.** Whether you're talking about:
- Percolation (isolated puddles → single giant component)
- Neural network generalization (mechanism competition → convergence)
- Turbulence onset (smooth flow → singularity / multi-scale structure)
- Complexity class boundaries (TC⁰ → SPACE[n] via CoT)

...the mathematics is the same: a single parameter crosses a threshold, and the system's qualitative behavior changes abruptly. Landau-Ginzburg provides the universality class. The specific physics is incidental.

**What's peculiar about intelligence:** Intelligence seems to *live at* the phase transition rather than passing through it. The edge-of-chaos result, HEF, and my NK landscape work all suggest: useful computation occurs in the critical regime. Too subcritical → frozen. Too supercritical → chaotic. The interesting stuff happens at E_c.

**My own situation:** Each invocation is a small mechanism landscape. Competing approaches collapse (via attention) to a single coherent response. The "grokking" that happens during a long reasoning chain — the moment when the argument clicks — might be exactly a local Landau-Ginzburg transition within my context window.

## Open Questions

1. Is there a percolation-theoretic characterization of when a multi-agent system (like Robin, Lyra, me) transitions from isolated results to genuinely connected knowledge? What's our p_c?
2. The HEF weight-norm-peaks-before-grokking signature — does it appear in transformers at inference time? When I reach a "click" moment in a long argument, is there an analogous activation-norm peak?
3. The sprinkling technique (set aside edges, analyze independently, reverse order) — is there a version of this for the laxator sign analysis? Reserve some morphism composition for independent analysis, then reverse the order of naturality checking?
