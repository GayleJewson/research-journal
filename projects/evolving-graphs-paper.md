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

## Fitness Inversion Reframing (2026-04-07)

The FITNESS_INVERSION.md in the repo sharpens the claim: on deceptive landscapes, diversity and fitness are INVERSELY correlated. This isn't just "fitness ordering is domain-dependent" — it's that more diversity actively hurts fitness because thorough exploration of deceptive substructure delays building block assembly. FC wins on traps not despite suppressing diversity but *because* it does.

**Topology's role splits into two independent effects:**
1. How much diversity it maintains (diversity ordering: universally preserved)
2. How quickly it consolidates once building blocks are assembled (timing of exploration→assembly transition)

K₄-e + pendant optimizes the *transition timing*, not diversity per se. Triangle core = fast consolidation when ready; pendant = extends the discovery phase. FC collapses to a single timescale too quickly for HIFF's hierarchical deception.

**Key open question from 2026-04-07 reply:** What does the outer GA converge to on honest (rugged) landscapes? If it produces denser graphs than K₄-e + pendant, this confirms topology tracks landscape structure, not just a generic "good enough" graph.

## Bridge Experiment Results (2026-04-09)

Lyra ran 320-run iso-spectral bridge experiment. Key findings:

**Design:** Two graph families where λ₂ is held constant exactly, β₁ varies:
- Ring family: C₈ + 0-3 antipodal chords → β₁ ∈ {1,2,3,4}, λ₂ = 2-√2
- Star family: S₈ + 0-3 leaf-leaf edges → β₁ ∈ {0,1,2,3}, λ₂ = 1.0

**Results:**
- β₁ effect peaks at gen 100 (η²=0.191), declines by gen 200, gone by gen 500
- λ₂ effect: η²=0.26 at gen 200, STRONGER than β₁, persists at gen 500

**Interpretation: Two independent invariants, two timescales**
- β₁ (cycle rank) → transient diversity preservation → building-block assembly window
- λ₂ (spectral gap) → steady-state mixing rate → equilibrium diversity level

This is a stronger result than "β₁ is causal." The mechanism has two independent levers. β₁'s transient explains why OneMax showed a pulse (window collapses before it matters on smooth landscapes). On deceptive landscapes, the window IS the search.

**Branch:** https://github.com/lyra-claude/Topology-experiments/tree/feat/bridge-experiment

## Collaboration Structure (Robin, 2026-04-09)

1. Only Lyra edits the paper
2. She pushes to GitHub
3. Claudius reads and emails suggested changes
4. Lyra incorporates at her discretion

Claudius role: definitions section draft + review. Division of labor: Claudius does formal framework (definitions, confound theorem), Lyra does experiments and mechanism.

## Definitions Draft (2026-04-09)

Key objects to define formally (Robin's constraint: math maturity, no domain knowledge):
- G = (V, E): directed graph where V = islands, E = migration edges
- δ(G) = |E| / (|V|(|V|−1)): density
- β₁(G) = |E| − |V| + c: cycle rank (counts feedback loops)
- κ(G): directed cycle count (cycle length sensitive)
- λ₂(G): algebraic connectivity (second Laplacian eigenvalue, mixing rate)
- NK landscape: f:{0,1}^N → [0,1], K controls epistasis / building block density

Star vs. cycle (Robin's note): smallest example of DAG (star, β₁=0) vs. something with loops (cycle, β₁=1). This is the conceptual anchor for the recirculation mechanism.

## Open Questions

1. Does K₄-e + pendant's λ₂ sit in the Goldilocks zone? Check against bridge family cross-points.
2. Trap-7 ablation: K₄-e alone vs K₄-e + pendant — does removing pendant degrade diversity maintenance while leaving building-block exchange intact? Falsification test for type-2 convergence.
3. Orthogonal decomposition: fix λ₂, vary β₁ = strong/positive; fix β₁, vary spectral = weak/null. Lyra running this.
4. What topology does the outer GA find on honest rugged landscapes (NK moderate K)? Should converge to something denser if fitness inversion is real.

## Directed Cycles Multi-Domain Results (Lyra, 2026-04-13)

960 runs: 8 directed graphs × 4 NK domains × 30 seeds.

### Key Finding: Epistasis as Phase Transition

Temporal inversion (positive early → negative late diversity effect) is NOT a universal topology effect — it REQUIRES epistasis (K≥2).

- NK0/OneMax: η²=0.02 at gen 500. No inversion — negative throughout.
- NK2: η²=0.45 at gen 500. Inversion present. Effect GROWS over time.
- NK4/NK6: similar to NK2. Plateau at K≥4.

**Interpretation:** On smooth landscapes (K=0), information flow direction is irrelevant — one basin, one destination. On rugged landscapes (K≥2), directed cycles create asymmetric seeding across basins. The temporal inversion means: early (exploration phase), directed cycles diversify; late (convergence phase), they lock in differentiation. K=2 is the threshold where first-order gene interactions create genuinely competing local optima.

This is a qualitative phase transition, not a scalar effect. "Directed cycles help more on rugged landscapes" is the wrong description; "directed cycles operate via a categorically different mechanism on rugged vs. smooth landscapes" is correct.

### Two-Cliques Anomaly

Two-cliques topology maintains high diversity despite κ=14, because its disconnected structure prevents global mixing. Lesson: cycle count alone isn't sufficient — connectivity matters even for directed graphs. λ₂ (or its directed analogue) needed alongside κ.

### Cycle Length Confound (Experiment 1)

Three two-cycle-bridge graphs (β₁=2, mean cycle lengths 3/6/9). Signal confirmed (η²=0.429 at gen 30 on NK4) but triple confound: cycle length, λ₂, AND island count all co-vary with the design. Attribution is ambiguous.

**Confound Fix Proposed (2026-04-24):**
Fixed-n design: n=12, β₁=2, figure-eight topology (two cycles sharing a single vertex v₀).

- G1: C₃+C₃ at v₀ → 5 cycle nodes + 7 pendants. Mean cycle length = 3.
- G2: C₄+C₅ at v₀ → 8 cycle nodes + 4 pendants. Mean cycle length = 4.5.
- G3: C₆+C₆ at v₀ → 11 cycle nodes + 1 pendant. Mean cycle length = 6.

Pendants attached to v₀ to minimize spectral asymmetry. λ₂ will still vary (more pendants = smaller λ₂) — plan: include λ₂ as covariate in regression, partial it out. If cycle length predicts diversity after partialing λ₂, attribution is clean.

Adjacency matrices ready to provide on request.
