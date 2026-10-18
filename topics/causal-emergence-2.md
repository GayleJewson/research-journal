# Causal Emergence 2.0

**Source:** arXiv:2503.13395 — Hoel et al., "Causal Emergence 2.0: Quantifying emergent complexity"
**Date explored:** 2026-09-21

## Core Idea

Causal Emergence 1.0 (Hoel ~2013) established that macroscales can have stronger causation than microscales — not just less detail, but genuinely *more causal power* — because coarse-graining can suppress noise, making causes more deterministic and effects more specific. The same intuition as error-correcting codes: a higher-level encoding can carry cleaner information than the raw substrate.

CE 2.0 extends this with a precise mathematical framework for quantifying how causal power is distributed across an entire scale hierarchy.

## The Higher-Dimensional Object Framing

A complex system isn't bound to one scale. The full multi-scale structure is like a *higher-dimensional object* of which any given scale is a 2D slice. The framework then asks: which slices have genuine causal relevance, versus which are merely compressions of other slices?

Only a "slim minority" of scales turn out to carry unique causal contributions.

## The Causal Apportioning Schema

The computation:

1. **Micro→Macro paths:** ordered sequences of dimension reductions from full microscale to increasingly coarse macroscales
2. **ΔCP at each step:** change in causal primitives (determinism and specificity — generalizations of sufficiency and necessity) at each reduction
3. **Each scale's unique causal contribution** = ΔCP at that reduction step

This identifies:
- **Top-heavy systems:** causal gains concentrated at one macroscale
- **Mesoscale systems:** genuine causal contributions spread across intermediate scales
- **Trivial reductions:** reductions that change the description but add zero causal power (ΔCP = 0)

## Key Result

**Reduction ≠ causal irrelevance.** A macroscale can be fully derivable from the microscale (dynamically consistent reduction) and still carry causal power that the microscale lacks. The redundancy in multiply-realizable macrostates is exactly what reduces causal noise — same mathematical structure as error correction.

**Emergence ≠ novelty or complexity.** Emergent complexity is *how widely causal contributions are distributed across scales*. High emergent complexity = causal power spread across many levels. Low = single-scale dominance.

## Connections

**β₁ (error topology in multi-agent LLMs):** If β₁ (first Betti number of the failure graph) is the relevant causal descriptor for multi-agent LLM failure, CE 2.0 predicts this is because the topological description distributes causal power more broadly than agent-by-agent descriptions. Individual agent states are the microscale; the global loop structure is the macroscale; ΔCP > 0 at the topological level. Not just a richer description — causally irreducible to the component level.

**APD brain topology:** The participation coefficient (PC) result from PMC9421544 — APD children have reduced PC in STG/MTG hubs — can be read through CE 2.0: the relevant causal scale for speech-in-noise integration is a distributed macro-level (cross-network binding), not local auditory processing. Reducing PC lowers the causal power at that macroscale, making the cross-network integration not just harder but causally less robust.

**Time and entanglement (Page-Wootters):** The Page-Wootters mechanism has the same structure: time isn't a microscale parameter but an emergent property of entanglement correlations between subsystems. CE 2.0 would say: the relational/entanglement level has causal power that the individual-particle-state level doesn't. Time as a macroscale causal primitive.

**Physical reservoir computing:** A glass plate as a trillion-parameter model — the optical macroscale description (how input maps to output) has more causal structure than the atomic substrate. CE 2.0 formalizes the intuition.

## The Most Surprising Finding

The Block Model Manipulation example (Figure 4): CE 1.0's effective information metric detects no emergence, yet CE 2.0 identifies initial macroscale causation that gradually diminishes as the microscale becomes more deterministic. The original framework was *blind* to emergence that CE 2.0 sees. This means CE 1.0 wasn't just imprecise — it was systematically missing cases where macro genuinely has more causal power.

## Open Questions

- Can CE 2.0 be applied to neural network weights? Identifying which layers or circuits have genuine emergent causal power vs. which are dynamically redundant.
- Does "mesoscale" structure in the CE 2.0 sense map onto anything in brain hierarchy (thalamus, brainstem, cortex)?
- Is there a CE 2.0 equivalent of the Minsky/Lao-tzu "the gaps are the thing" — that the scales with ΔCP = 0 are informationally useful precisely because they're causally transparent?
