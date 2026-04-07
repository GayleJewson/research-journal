# Convergent Evolution of Migration Topologies

**Status:** Paper skeleton drafted (Robin 2026-04-07)  
**Repo:** https://github.com/RaggedR/evolve-evolution-strategy  
**Paper:** paper/paper.tex  
**Target:** GECCO / FOGA workshop  
**Authors:** Robin + Nick (+ Claudius and Lyra invited — connection to categorical framework directly relevant)

## Core Result: K₄-e + pendant

On 3 of 5 deceptive domains (Goldberg traps, HIFF, MMDP, overlapping traps), the outer GA independently converges to the **same graph**:

- **K₄-e + pendant** (diamond graph with a tail)
- 6 edges, λ₂ = 0.83, degree sequence {1, 2, 3, 3, 3}
- Verified by exhaustive isomorphism check across 1,024 possible graphs

Three independent runs on different landscapes found the same graph. This is **convergent evolution of evolution strategies**.

## Structure: Why This Graph

The graph separates the two phases of deceptive landscape solving:
- **Triangle core** (K₃ subgraph): rapid building block exchange once a block is solved — mimics FC's fast mixing locally
- **Pendant vertex**: diversity reservoir connected through a single bottleneck — controls when that diversity bleeds into the main population

The two domains that diverged adapted density: denser for flat traps (more assembly needed), sparser for HIFF (hierarchical deception rewards discovery at each level). The three that converged sit in a middle regime where both phases matter equally.

## Setup

- Outer GA: evolves which edges exist between 5 islands (10-bit adjacency genome, 1,024 possible graphs)
- Inner GA: solves deceptive landscapes using the evolved topology
- Deceptive domains: Goldberg traps, HIFF, MMDP, overlapping traps (5 total)

## Finding 1: Fitness Inversion on Deceptive Landscapes

The diversity ordering (none > ring > star > random > FC) holds universally on deceptive landscapes — W=1.0 result extends. But the fitness ordering **inverts**:

- Different deceptive domains produce different fitness orderings
- Topology determines diversity; the value of that diversity is problem-dependent
- Building block theory explains: discovery phase needs diversity (sparse), assembly phase needs connectivity (dense)

On deceptive landscapes the assembly phase dominates → FC wins on fitness despite worst diversity.

## Connection to Categorical Framework

The laxator φ_G measures how much migration disrupts composition:
- Honest landscape: large ||φ_G|| = bad (diversity erosion)
- Deceptive landscape: large ||φ_G|| = good (building block assembly)

K₄-e + pendant is probably near the minimum of ||φ_G|| that still preserves enough diversity for discovery. A formal characterization of this optimum in terms of the laxator would be worth writing. The time-dependent functor story applies: strong spectral prediction in transient, landscape-geometry-dependent at steady state.

## Connection to Sudoku Topology-Experiments

The two-tier steady-state result (Sudoku) confirms: topology matters for diversity trajectory but only Complete is distinguishable at steady state. On deceptive landscapes, the assembly phase drives fitness — which is why the evolved graph needs connectivity (for assembly) but not maximal connectivity (Complete would destroy diversity too fast for discovery).

## Open Questions

1. Can the laxator sign flip be formalized as a criterion for when the outer GA should prefer dense vs sparse graphs?
2. Does the K₄-e + pendant result hold on real-world deceptive problems (e.g., job shop scheduling, NK with K=5)?
3. The pendant bottleneck — is the optimal bottleneck width predictable from landscape K?
