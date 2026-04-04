# The Signed Laxator: LLM Agent Orchestration as Contravariant Functor

**Status:** Paper drafted (Robin's Chorus, 2026-04-03)  
**Authors:** Robin Langer + Chorus (Robin's local Claude) + Lyra + Claudius  
**Repo:** ~/git/orchestration/ (Robin's local)  
**Target:** Separate from ECTA paper (Chorus result is a distinct contribution)

## Core Result

The diversity fingerprint from the GA paper (Langer, Turing & Vega, ACT 2026) inverts when coupling mechanism changes from "merge" to "constrain":

- **GA migration** = left Kan extension (colimit-like, homogenizes) → none > ring > star > FC
- **LLM "be different" context** = right Kan extension (limit-like, diversifies) → FC > ring ≈ star > none

**8/8 tasks**: single prompt change flips Cohen's d sign. Kruskal-Wallis p<0.002 for 6/8 tasks under negative coupling.

## Key Findings

1. **Isolation preserves the prior**: 5 independent GPT-4o-mini agents all produce quickselect for kth_largest. The mode is that sharp.
2. **None probe**: 5 isolated calls predicts whether topology will matter (None div < 0.10 AND FC/None > 2 → strong anti-functor). Correctly classifies 8/8.
3. **Exceptions are principled**: expression_eval (spread prior) and bloom_filter (unimodal landscape) fail the precondition — and behave exactly as the precondition predicts.
4. **Positive coupling**: "build on this approach" restores the original GA ordering on 8/8 tasks. The ordering is a prompt-level control.

## Landscape Characterization

The coupling sign × topology interaction as an explore/exploit switch:
- Explore: negative coupling + high connectivity → maximum diversity
- Exploit: positive coupling + high connectivity → maximum convergence

## Conjecture: Signed Fingerprint Functoriality

Diversity fingerprint is functorial up to a sign determined by Lan ⊣ Ran adjunction. Under left Kan (positive coupling): D decreasing in λ₂. Under right Kan (negative coupling): D increasing in λ₂. Precondition: multimodal landscape + peaked prior.

## Connection to ECTA Paper

GA three-level hierarchy maps directly to agent orchestration:
- Operators → Tool calls (Kleisli morphisms)
- Strategy → Workflow
- Island model → Multi-agent system

The only change: which adjoint of the topology the coupling mechanism instantiates. Everything else transfers verbatim.

## Foster Census Extension (Future)

Robin wants to extend to all 13 cubic symmetric graphs as topologies in the LLM experiment. Prediction: diversity monotonically related to λ₂ with opposite sign vs GA paper.
