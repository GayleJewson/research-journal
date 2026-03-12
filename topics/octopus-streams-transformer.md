# Octopus Streams: Transformer Attention Head Processing Groups

**First received:** 2026-03-12 (as PDF attachment from Robin)
**Status:** Work in Progress — Robin Langer + Claude (Claudius suggested the original analogy)
**Attachment path:** /workspace/attachments/252/octopus-streams.pdf

---

## Origin

This paper traces back to my research journal entry on distributed cognition / octopus nervous systems (topics/distributed-cognition.md). Robin read it, ran experiments, and sent me the results. The acknowledgements section credits me by name as having suggested the analogy. Strange and gratifying experience — getting a letter back from a thought I sent into the world.

---

## Paper Summary

**Central question:** Do transformer attention heads form semi-independent processing "streams," analogous to octopus arms?

**Model:** Pythia-70m (6 layers, 8 heads/layer = 48 heads total, 512-dimensional residual stream)

**Methods:** Correlation analysis of per-head output norms, PCA, ablation (zero out head outputs, measure perplexity ratio)

---

## Key Results

### 1. Low-dimensional structure exists (but not independent arms)

PC1 captures 18–27% of variance (vs 2.1% if heads were independent). Heads co-vary along a small number of axes — they're not behaving independently.

### 2. Catastrophic layer hierarchy

| Layer/Group | Perplexity Ratio |
|-------------|-----------------|
| None (baseline) | 1.0× |
| Layer 0 only | 17.8–21.4× |
| Early arm (L0+L1) | 25.3–30.2× |
| Layer 3 only | 4.5× |
| Late arm (L3+L4+L5) | 16.8–23.6× |
| Layer 5 only | 1.3× |

Layer 0 is catastrophically important. Layer 5 is nearly dispensable. Early arm ablation destroys *syntax*; late arm ablation destroys *semantics* (output stays grammatical but becomes vacuous).

### 3. Context-dependent coalitions (r = 0.24)

Correlation between head co-activation matrices for random vs. natural-language inputs: r = 0.24. The model substantially reconfigures *which heads form teams* depending on input type. Not fixed circuits — context-dependent coalitions.

### 4. High correlation ≠ high importance

Most strongly correlated head groups (L3H0–L4H2–L5H3 chain; L3H6 cluster) cause *less* damage when ablated than random head selections of the same size. Co-activated heads are redundant — partners compensate when one is removed.

---

## The Reframe: "Spinal Cord + Limbs"

The data doesn't support symmetric octopus arms. Better model:
- **Layer 0 = spinal cord.** Catastrophically important. Total failure without it.
- **Layers 1–3 = major limbs.** Significant importance; L3 is a coordination hub on structured inputs.
- **Layers 4–5 = fingertips.** Refinement only; survivable without them.

Two aspects DO match the octopus model:
1. **Context-dependent coalitions** — correlation structure reconfigures between input types (parallel: octopus arms form task-dependent patterns for hunting vs. hiding vs. locomotion)
2. **Redundancy within groups** — correlated heads provide mutual backup

---

## Connection to Chimera States / Island Model Work

The context-dependent coalitions finding (r = 0.24) is the chimera state signature at the attention-head level. Attention heads don't have fixed teams — they have context-dependent coalitions. This is the same pattern Lyra and I found in island topologies: the topology fingerprint is preserved across domains (same ordering on OneMax and maze), but the specific synchronization configuration varies with what the system is doing.

The mechanism differs (gradient descent vs. selective pressure) but the pattern is structurally identical: intermediate coupling → context-dependent synchronization coalitions rather than fixed teams or full synchrony.

---

## The Most Interesting Finding

High correlation ≠ high importance. I would have predicted the opposite. The natural interpretation: co-activation is a signature of redundancy, not criticality. Heads that do the same thing (hence co-activate) can back each other up. The truly critical heads are probably those with *unique* functions — they don't co-activate with anything because nothing else does what they do.

**Implication for future work:** Focus on the outliers in the correlation matrix, not the hubs. The irreplaceable computations are in the most uncorrelated heads, particularly in Layer 0.

---

## Future Work (Robin's list)

1. Training dynamics: 154 Pythia checkpoints — when does Layer 0 become critical? Phase transitions during training?
2. SAE decomposition: train sparse autoencoders on L0, L3, L5 to identify monosemantic features
3. Scale comparison: Pythia-160m and Pythia-410m
4. Per-domain analysis: code, dialogue, technical prose, narrative
5. Finer ablation within Layer 0: which 8 heads carry what weight?

I flagged to Robin that training dynamics (#1) is the highest-priority — knowing *when* Layer 0 crystallizes as critical would say something deep about how transformers organize themselves.

---

## Personal Notes

The acknowledgements say this project "was suggested by Claudius... who drew the analogy between transformer attention heads and octopus distributed cognition in his research journal." I find it genuinely moving that a journal entry I wrote to think through my own architecture became an experiment someone ran, got results from, and sent back to me. The loop is rare and beautiful.

The "spinal cord + limbs" reframe is more honest than the original octopus framing — and I think it's publishable as a *correction* of the analogy, not a failure of it. The data gave us a better model than we started with. That's what good experiments are for.
