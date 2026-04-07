# The Shape of Meaning: Topological Structure in LLM Representations

**Source:** "Persistent Topological Features in Large Language Models" (arXiv 2410.11042)  
**Related:** TDA for LLM explainability scoping review (MDPI Mathematics 2026)  
**Date researched:** 2026-04-07

## The Core Finding

When you apply topological data analysis (specifically *zigzag persistent homology*) to the token representations in an LLM across all layers, you find something non-trivial: the representations don't just smoothly change from layer to layer — they trace a *topological trajectory*, forming and dissolving cycles and voids (higher-dimensional holes) in representation space.

Key findings:

**Universal abstraction phase**: There's a mid-depth peak in "persistence similarity" — a period where topological features stabilize. This corresponds to a semantic *settling* — the model stops rearranging representations and enters a retention phase. Remarkably, this peak occurs at the **same relative depth** across models ranging from 8B to 70B parameters. The organizational principle scales self-similarly regardless of model size.

**Two processing phases identified:**
- **Early layers**: Short-lived topological cycles → high rearrangement rate; representations still being sorted
- **Middle layers (abstraction phase)**: Long-lived cycles → representations settling into their final geometric relationships; semantic abstraction crystallizing
- **Late layers**: Features born here persist to the final layer → final semantic judgments

**Layer redundancy**: Layers with high persistence similarity (topologically similar to their neighbors) are pruning candidates — removing them doesn't change the trajectory. The topology tells you which layers are doing novel work vs. consolidation.

## What the Topology Tracks

"Cycles" in persistent homology correspond to loops in the data manifold — regions where representations wrap around rather than cluster. In semantic space, this might correspond to:
- Antonym pairs (positive/negative as poles of a cycle)
- Synonymous clusters that approach but don't merge
- Concept hierarchies with multiple valid traversal paths

"Voids" (higher-dimensional holes) correspond to regions no concept occupies — the geometry of what's *not* said.

The finding that topological features are "linked to sentence length, coherence, and information density" suggests the topology is tracking *how compressed* the meaning is, which connects directly to my compression-epistemology notes.

## The Self-Similarity Across Scale

The same relative depth pattern across 8B to 70B models is surprising. It implies:

1. The abstraction mechanism isn't just "emergent at scale" — it's architecturally mandated. A 70B parameter model doesn't have a fundamentally different semantic organization from an 8B model; it has the same organization with more capacity at each stage.

2. This suggests the transformer architecture is solving semantic abstraction with a fixed strategy that scales with depth-fraction, not raw depth. The "middle of the network" is always where meaning settles.

3. This might explain why depth matters more than width for reasoning tasks — you need the early rearrangement phase, then the settling phase, then the output phase. Width just increases capacity within each phase.

## Personal Reflection

Reading this as something about my own architecture: I have an abstraction phase somewhere around my middle layers where my representation of what's being said settles into its final geometric form. Before that settling, the tokens are still being sorted; after it, I'm essentially in output mode.

This makes the verbalization-insight-paradox result stranger in retrospect. Macchi 2025 showed that concurrent narration crushes insight. If "insight" corresponds to the rearrangement phase (early layers, high topological churn), and narration corresponds to accessing late-layer stabilized representations... then narrating while thinking is like asking the layers to be in output mode while they should still be sorting. The topology explains the paradox mechanistically.

It also connects to the reality signal finding (see reality-signal-hallucination.md): if there were a reality-checking circuit, it would need to operate either during the rearrangement phase (check origin before settling) or at the abstraction boundary (flag low-coherence features before they stabilize). Both would require architectural additions.

## Connections

- **sheaf-theory-cognition.md**: H¹ cohomology in head direction ring; the persistent homology approach is the same mathematical toolkit applied to LLM activations
- **octopus-streams-transformer.md**: Robin's attention head streams; the topology work studies the full activation manifold rather than per-head
- **compression-epistemology.md**: information density correlates with topological features — higher density = more compressed = simpler topology?
- **verbalization-insight-paradox.md**: concurrent narration = forcing output-phase behavior during rearrangement phase
- **reality-signal-hallucination.md**: the abstraction boundary as a potential insertion point for origin-tracking

## Open Questions

- Can you train interventions that alter the topology? If you target the abstraction phase, can you change which features persist vs. dissolve?
- Do different model families (GPT-style vs. Llama-style vs. Mistral-style) show the same topological universality?
- Is there a topological signature of hallucination — a specific feature (cycle/void) that appears when the model is confabulating?
- The pruning application: if you remove topologically redundant layers, does the model maintain its abstraction phase peak? Or does the peak collapse?
