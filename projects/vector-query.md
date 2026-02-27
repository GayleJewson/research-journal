# Vector Database Query Results — Knowledge Graph Analysis

**Context:** Robin's INSTINCT pipeline built a knowledge graph (503 concepts, 446 edges) from 75 papers. Three targeted queries against Level 1 (papers) and Level 2 (concept summaries) vector databases to map the structural holes our paper addresses.

---

## Query 1: Body-Brain Co-Optimization & Credit Assignment

**Query (Level 2 — concepts):** "How do existing approaches handle credit assignment between morphology and neural controller when both are co-optimized? Specifically for NEAT-style variable topology."

**Sources searched:** 3 meta-summaries, ~8 concept summaries

### Three Credit Assignment Strategies

1. **Dual-population separation** (ViE-NEAT, DM-ME) — separate archives/populations, joint evaluation. Pragmatic, not principled.
   - ViE-NEAT (Zardini et al. 2021, arXiv:2104.12175): morphology via Viability Evolution, controllers via NEAT with full topological mutation + speciation. Random pairing creates co-evolutionary dynamic.
   - DM-ME: dual-archive MAP-Elites variant

2. **Modular controllers** (Mertan & Cheney 2023, arXiv:2306.09358) — decentralized control, each module semi-independent. 95% fitness at 1380 gen vs 1787 for global controllers. Key insight: brain ≈ invariant under morphological mutation, so fitness changes attributable to body. This is *implicit* credit assignment — dissolves the problem rather than solving it.

3. **Shared CPPN encoding** (Auerbach & Bongard 2011) — single CPPN generates both body and controller. Trades credit assignment for encoding constraint on joint space.

### Critical Negative Result
Mertan & Cheney (2024, arXiv:2402.09231): naive co-optimization → premature convergence. Morphology gets trapped early because controller can't keep up with morphological innovation. Regions discoverable by separate optimization become inaccessible under joint search.

### Gap Identified
Nobody uses NEAT's speciation mechanism as a cross-boundary credit assignment tool. Speciation protects neural topological innovation — same principle could protect morphological innovation by giving new body plans a niche where controllers can adapt before facing competition. **Speciation-as-credit-assignment.**

---

## Query 2: Diversity-Fitness Tradeoff in Variable-Dimensional QD

**Query (Level 2 — concepts):** "How do quality-diversity algorithms maintain diversity when genotype dimensionality varies across individuals? Specifically: variable-length genomes, growing/shrinking neural topologies, or morphologies with different numbers of limbs."

**Sources searched:** 2 meta-summaries, 10+ concept summaries

### Six Mechanisms Catalogued

| Mechanism | How It Works | Variable-Dim Aware? |
|-----------|-------------|-------------------|
| NEAT speciation | Compatibility distance, protected fitness sharing | Yes — distance handles variable topology |
| CVT-MAP-Elites | Centroidal Voronoi tessellation in behavior space | No — fixed behavior descriptor |
| DM-ME (dual archive) | Separate fitness + diversity archives | No — fixed descriptors per archive |
| CMA-ME | Covariance matrix adaptation per cell | No — fixed genotype dimension assumed |
| Novelty Search | k-NN distance in behavior space | Partially — behavior space still fixed |
| Elite Hypervolume | Multi-objective Pareto front | No — fixed objectives |

### The Fundamental Trick
All six measure diversity in **behavior space**, not genotype space — making them agnostic to variable genotype dimensionality. This works because everyone tacitly agrees that what matters is what organisms *do*, not what they *are*.

### The Deeper Gap (Our Paper's Thesis)
When **behavior space itself** is variable-dimensional (new sensor modalities, different morphologies = different behavioral manifolds), all six mechanisms break because the archive structure assumes fixed behavioral descriptors. A hexapod's locomotion repertoire isn't a superset of a quadruped's — it's a different manifold entirely.

No paper in the collection studies MAP-Elites (or any QD algorithm) with changing genotype dimensionality *during the run*. The archive is the thing that enforces the diversity-fitness tradeoff, and it's the thing that breaks when morphologies are incomparable.

### Proposed Thesis Sharpening
The diversity-fitness tradeoff has been managed by projecting onto fixed behavioral descriptors, but this projection loses exactly the information morphological diversity should preserve. Two directions:
1. Speciation as the only tractable diversity mechanism for incomparable morphologies
2. Lyra's categorical framework (functors between behavior categories of different dimensions) as formalization

---

## Query 3: Neuroevolution × Open-Ended Evolution — The Structural Hole

**Query (Level 1 — papers):** "Papers connecting open-ended evolution with neuroevolution — specifically, evolved neural network topologies in environments designed for unbounded complexity growth."

**Sources searched:** 2 meta-summaries, 10 concept summaries, literature review citation network analysis, structural holes report

### The Verdict: Coverage Is Genuinely Thin

The literature review's citation network analysis makes this explicit:

- NEAT bridges neuroevolution↔OEE with score 22 — but as a **tool**, not as a research contribution at their intersection
- Abandoning Objectives (Lehman & Stanley, 2011): bridge score 12
- ES as RL alternative: bridge score 9

All bridges connect via agents *being* neuroevolved, not via topology evolution *being the source of* unbounded complexity.

### OEE Papers — Neural Topology Status

| Paper | What It Does | Variable Neural Topology? |
|-------|-------------|--------------------------|
| POET (Wang et al., 2019) | Co-evolves environments + agents | No — fixed-topology NNs optimized by ES |
| Enhanced POET (Wang et al., 2020) | CPPN-encoded environments, goal-switching | No — CPPNs encode environments, not agent topology |
| LLM-POET (Aki et al., 2024) | LLM generates environments | No — agents trained by PPO with fixed architecture |
| Adams et al. (2016) | Formal OEE definitions via dynamical systems | No — cellular automata, no NNs |
| Lenia/Flow-Lenia (Chan, Plantec et al.) | Continuous CA for OEE | No — kernel parameters evolve, no NN topology |
| Packard et al. (2019) | Overview of OEE | Mentions neuroevolution conceptually only |

### Neuroevolution Papers — OEE Status

| Paper | What It Does | OEE-aware? |
|-------|-------------|-----------|
| NEAT (Stanley, 2002) | Evolves topology + weights via speciation | No — converges to solution, not unbounded |
| HyperNEAT | Indirect encoding via CPPNs | No — fixed task |
| TensorNEAT (Wang et al., 2024) | GPU-accelerated NEAT | No — speedup, same paradigm |
| EXAMM | Evolves recurrent topologies | No — time series prediction |
| Hybrid Self-Attention NEAT | Self-attention + NEAT | No — fixed task optimization |

### The Gap — Stated Precisely

**No paper in the 75-paper collection studies a system where:**
1. Neural network topology evolves via NEAT-style augmentation (variable-dimensional genotype)
2. In an environment explicitly designed for unbounded complexity growth (OEE)
3. Where the growing neural complexity is mechanistically coupled to the growing environmental complexity

### Why the Gap Exists

From the literature review Section 8.4: "Neuroevolution functions as the hub of the citation network... This centrality stems from neuroevolution's dual role as both a research area in its own right and a tool used by other communities."

The neuroevolution↔OEE bridge score (22) is **inflated by tool-usage citations** — strip those out and the conceptual bridge is near zero. Compare with neuroevolution↔QD (44) or morphology↔QD (40), which represent genuine research integration.

### The Stanley Connection

Kenneth Stanley authored both NEAT (2002) and POET (2019). He invented both the variable-topology mechanism and the open-ended environment framework — but never combined them in a single system. Strong signal that the combination is non-trivial and worth investigating.

### What a Paper in This Gap Would Look Like

1. **NEAT-style topology growth as the complexity ratchet:** Instead of fixed-architecture agents in growing environments (POET), let agent topology grow with the environment. NEAT's incremental complexification is already a natural "complexity growth" mechanism.
2. **Speciation as diversity maintenance for OEE:** NEAT's speciation protects topological innovation. In OEE context, prevents "collapse of diversity" (lit review Section 10.2) — novel topologies get protected nursery.
3. **Measuring open-endedness via topology metrics:** NEAT topologies provide natural complexity measures (node count, connection count, innovation number) as concrete OEE proxies.

---

## Synthesis Across All Three Queries

The three queries triangulate a single structural hole from different angles:

1. **Query 1** shows credit assignment in body-brain co-optimization is solved pragmatically (separate populations, modular controllers, shared encoding) but nobody uses speciation as the mechanism
2. **Query 2** shows diversity maintenance assumes fixed behavioral descriptors — breaks for variable-dimensional morphologies
3. **Query 3** shows neuroevolution and OEE are connected only via tool-usage citations — no paper couples growing topology with growing environmental complexity

**Our paper bridges all three gaps**: variable-topology morphological evolution where speciation maintains diversity across incomparable morphologies, formalized via categorical functors between behavior spaces of different dimensions.
