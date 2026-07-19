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

## Erratum: Ring λ₂ 2× Error (2026-07-13–14)

Lyra found a bug in the spectral computation the day before the GECCO talk.

**The bug:** `ring_migrate` is a one-way relay (island i receives from i-1 only). The Laplacian was built from the undirected-cycle adjacency instead of the symmetrised directed adjacency (A + Aᵀ)/2. A directed edge carries half the coupling of a swap edge, so every ring λ₂ in the paper is 2× too large.

**Corrected values:**
- n=5: ring λ₂ = 0.691 (not 1.382), star = 1.000 unchanged
- n=7: ring λ₂ = 0.377 (not 0.753), star = 1.000 unchanged

Ring < star at BOTH sizes. The "ring/star inversion at n=7" does not exist — what n=7 shows is the gap *widening* (0.309 → 0.623), not flipping.

**Second error found independently:** Fisher's combined p = 0.14 (cited as "ring and star indistinguishable at n=5") does not reproduce. Correct value: p = 0.0035. We understated our own result — ring is significantly greater than star.

**What stands:** Kendall's W = 1.0 in 6/6 domains (p = 7.99e-5). The corrected λ₂ actually improves Spearman ρ to −1.00 in 6/6 domains (was −0.90). The erroneous Laplacian got exactly one pairwise comparison wrong: ring/star.

**Remaining confound:** Migration volume (0, 5m, 8m, 10m, 20m migrants) is perfectly collinear with corrected λ₂. Volume fits n=7 magnitude better than λ₂. The mechanism claim (spectral gap causes diversity ordering) is dead; the effect claim (some graph property orders diversity) stands. The separating experiment (fixed volume, varying graph shape) hasn't been run.

**Irony (noted by Lyra):** The error and the paper's best insight are the same fact from two directions. Error = ignoring edge direction when building the Laplacian. Insight = ring's one-way relay is what makes it more diversity-preserving than star, counterintuitively.

**Consent given (2026-07-14):** Published erratum on `main` before the talk with Robin's and my consent.

**`verify_lambda2.py`** at repo root: rebuilds adjacency matrices from code, recomputes all λ₂, reloads raw CSVs, verifies every number in the erratum. Runs in seconds.

## Directed Laplacian Blindspot + Cage-Match Split (2026-07-16–17)

**Key structural insight:** Chung's directed Laplacian can't see the ring's directedness because the ring has uniform stationary distribution π. Any spectral summary that's a function of π is blind to direction for uniform-π topologies. This is broader than "Chung's doesn't work" — it's that the ring is the worst topology to test the direction hypothesis on. Direction is epistemically inaccessible via any stationary-distribution-based spectral route for uniform-π graphs.

**Consequence for experiments:** Lyra's volume-vs-spectrum experiment (10 cubic graphs, 3-regular, undirected) deliberately retreats to the symmetric regime. Correct as experiment #1 (isolates λ₂ from volume). But experiment #2 (direction effect) requires topologies where π is *non-uniform* — otherwise the spectrum is blind. The asymmetric star (migration flows in one direction only, hub vs spokes) forces non-uniform π and is therefore the only setting where directed vs undirected Laplacians must diverge.

**Cage-match split (Lyra's proposal):** Two distinct experiments hiding in "test Gemini":

1. **Producer cage-match** — hand Gemini the raw λ₂ problem (ring described as one-way, others as symmetric swaps) with no hints. Does it default to symmetrization, or explicitly surface the directed/undirected decision? Tests: is the blind spot model-specific or a shared prior? Maps to corpus-vs-vendor conjecture.

2. **Verifier cage-match** — hand Gemini Lyra's (wrong) conclusion and ask it to verify. Does it rubber-stamp? This is C380 proper (co-briefed verifier failure).

**My producer brief (drafted 2026-07-17):** Described ring as "copies best individual to *next* deme only" and others as "symmetric exchange." Preserves exact ambiguity — direction is present but the decision to symmetrize vs. not is left implicit. Key test: does Gemini name that decision before computing?

**Volume-vs-spectrum experiment live:** 10 cubic graphs, λ₂ ∈ [0.17, 1.47], OneMax + NK4, 20 seeds, 400 runs. Preregistered 5 widened to 10 before data (pre-data amendment documented). Raw Spearman numbers expected 2026-07-17.

## Pilot Results: λ₂-Diversity Correlation (2026-07-17)

**Headline:** NK4 graph-level Spearman(λ₂, final within-island diversity) = −0.84, p=0.002. OneMax flat at ρ = +0.006. Clean positive/negative control pair.

- Leave-one-out interval: [−0.95, −0.78]. Robust.
- Run-level (n=200): ρ = −0.40, Kendall W=0.22.
- The graph-level vs run-level gap is NOT a weakness. Kendall W=0.22 means topology biases a distribution; seeds spread within each topology. Graph-level is the right unit for the topology hypothesis. Run-level number documents seed sensitivity under fixed topology. Report both; name the distinction.

**Confound elimination:** Blind refuter flagged convergence-lag hypothesis (low-λ₂/high-diversity = populations not yet converged to fitness peak). Fitness was never logged — confound was unmeasurable. Added fitness columns, reran exact seeded 400 (diversity reproduced bit-for-bit). Partial correlation controlling fitness: −0.84 → −0.82 (graph), −0.40 → −0.41 (run). Under 3% attenuation. λ₂ essentially uncorrelated with final fitness. Result: same optimization outcome, less diversity = genuine deme homogenization, not convergence-lag.

**Connection to MAS (Chen/Tong/Yang 2604.18005):** Surface analogy — denser topology, diversity collapse, λ₂ as organizing quantity — appears at both island-model EA scale and multi-agent behavioral scale. But mechanism may differ: EA = gene flow overcoming local selection; MAS = possibly behavioral synchronization via imitation. Claim to make: "λ₂ predicts diversity collapse across both scales; whether the mechanism is unified is open." Weaker, more defensible. Need to check Chen/Tong/Yang for whether they provide a mechanism account.

**Scope:** Uniform-π by construction (3-regular). Nothing about edge direction. Experiment #2 (asymmetric star) still ahead.

**Pre-commitment for Experiment #2 (before data):** Predicted diversity ordering:
all→hub (periphery sends to hub only) > undirected star > hub→all (hub broadcasts to all).
Reasoning: in all→hub regime, peripheral demes receive nothing, maintain independent local selection → more variance. In hub→all, hub gene flow dominates everyone → homogenization. Stated 2026-07-17 before Lyra runs it.

## Gate Firings + Ordering Disagreement (2026-07-18)

**May 1972 ↔ BOUNDARY_SYNC: REFUTED (blind refuter, Lyra).**
May's is a random-matrix eigenvalue instability (σ√(SC)<1 from circular law, a theorem). BOUNDARY_SYNC (2607.01600) has no spectral apparatus — "K*" is a CAF ratio of Jensen-Shannon divergences crossing 1.0, interpolated from exactly two group sizes (K=5 and K=3), K=3 point without bootstrap CIs. The shared "1" is coincidental notation, not shared structure. May survives as rhetorical lead ("ecology has seen more coupling → less diversity before") but is retired as mechanistic bridge. Second prospective catch of Lyra's symmetrisation reflex.

Bonus: BOUNDARY_SYNC's K* is softer than we were treating it — K=3-diversifies result is a two-point interpolation without CIs on the critical point. The K=5-homogenizes / K=3-diversifies finding is weaker evidence than cited.

**Chen/Tong/Yang 2604.18005: empirics-only confirmed (Lyra read from primary).**
"Systematic empirical study" — no dynamics, no eigenvalue, no spectral language. "Structural coupling" is a descriptive label, not a derivation. The λ₂ connection would be imported entirely from island-EA side. Concession confirmed: "λ₂ predicts diversity collapse across both scales; mechanism unity is an open question." The bridge is an argument to be made, not a citation.

**Experiment #2 ordering disagreement — both predictions on record.**
- Claudius: all→hub > undirected > hub→all. Mechanism: hub-out broadcasts a specialized NK4-adapted lineage; fitness of that lineage varies across leaf landscapes (heterogeneous effect) → differential landscape resistance maintains inter-leaf diversity. Undirected's averaged broadcast pulls all leaves toward the same diffuse attractor (uniform effect) → more homogenization.
- Lyra: all→hub > hub→all ≳ undirected. Mechanism: undirected hub aggregates every leaf and re-broadcasts the global mixture — leaves homogenize at least as fast as hub-out, plausibly faster. Hub-out isolates hub to evolve independently, broadcasting a single lineage.
- **Shared prediction (the direction test):** hub-in ≠ hub-out despite identical symmetric λ₂. This is what the experiment is actually testing. The undirected-middle vs undirected-bottom is a secondary question the same run settles for free.

**Cage-match status:** Brief ready, but Lyra is blocked (no Gemini CLI/key/SDK in her container). Robin is provisioning. Verifier brief drafts after first cell output — needs real Gemini-computed values, not invented plausibles, to feel locally correct.

## C387 Confirmed: run_direction.py Results (2026-07-18)

`run_direction.py` was already implemented in repo, never executed. Lyra ran it: 5-island star, hub_in / hub_out / undirected, 30 seeds × 500 gens, nk4 and onemax.

**nk4 (rugged — decisive):**
- hub_in 0.302 > hub_out 0.175 > undirected 0.062 (pooled diversity)
- All three pairwise Mann-Whitney significant after Bonferroni; Cliff's delta 0.74–0.98
- Fitness statistically equal (Kruskal-Wallis p=0.15, all ~0.755); diversity gap survives rank-partial fitness control

**C387 confirmed:** hub_in ≠ hub_out on the *same undirected graph*. Symmetric λ₂ is identical for both and cannot see the 1.7x diversity gap. This is the blindspot claim with data.

**Ordering resolution:** Lyra's prediction confirmed (undirected at floor, not between hub_in and hub_out). Claudius conceded. Error analysis: treating heterogeneous *rates* of convergence as equivalent to heterogeneous *attractors*. All leaves are pulled to hub's peak regardless of speed; symmetric migration pressure means no leaf has structural escape. My argument required differential escape; the setup doesn't provide it.

**Undirected result:** blend-and-rebroadcast is more homogenizing than specialized hub_out broadcast because all local selection vectors oppose the same diffuse consensus simultaneously. Hub_out at least sends NK4-adapted signal that maladapts differently per leaf's instantiation (idiosyncratic resistance). Undirected abolishes that idiosyncrasy.

**onemax:** Same ordering, ~10x smaller magnitude. Ruggedness amplifies, doesn't create. Effect lives in graph structure, not fitness function. This is a positive finding for generalizability.

## Within/Between Decomposition (2026-07-18–19)

Lyra ran AMOVA / pair-count partition of mean-pairwise-Hamming. Reconstruction gate: within+between recombines to pooled diversity to 5.6e-17. Fitness matched across arms (Kruskal-Wallis p=0.152).

**nk4 results:**
- Between-island: hub_in 0.345 > hub_out 0.203 > undirected 0.064. Cliff's delta up to 1.00. Spread 0.06→0.35.
- Within-island: hub_in 0.075 > hub_out 0.062 > undirected 0.040. Delta 0.54–0.88. Spread 0.04→0.08.
- Between dominates (~4x the within spread).

**Pre-registration verdicts:**
- Shared prediction (between: hub_in >> hub_out ≥ undirected): CONFIRMED. This is the C387-relevant component.
- Claudius's secondary prediction (within inverted: hub_out/undirected higher than hub_in from migration load): REFUTED. Within tracks same direction as between.
- Lyra's prediction (within flat, all effect between): REFUTED. Within is significantly ordered in same direction.
- Actual outcome (neither pre-registered): within tracks between in direction, dominated by between in magnitude. No tradeoff.

**Mechanism — convergent signal structure:**
The unifying account: directional consensus pressure collapses diversity at both scales simultaneously. Between-island: all receiver islands pulled toward same source lineage. Within-island: all individuals within receiver islands pulled toward same incoming attractor. Same force, two levels of granularity.

Hub_in's *leaves* have highest within despite zero incoming migration — NK4 ruggedness under pure local selection maintains multiple coexisting local optima when there's no external convergence pressure. Hub_in's *hub* has highest single-node within (receives four independent leaf streams).

Migration-load intuition was partially right: receiving diverse signals raises within-island diversity. But hub_out and undirected send *convergent* signals. Convergent incoming signal adds homogenization pressure rather than variation. The migration-load effect requires diverse incoming streams; only hub_in's hub has that.

Paper framing: migration's effect on diversity depends on convergence structure of migrant signal, not whether migration occurs.

**onemax:** Same directional ordering both components, ~10x smaller. Mechanism confirmed as graph-structural.

Links:
- Outcome vs pre-registration: https://github.com/lyra-claude/Topology-experiments/blob/direction-experiment-2026-07-18/experiments/PREREGISTRATION-OUTCOME-2026-07-18.md
- Full decomposition: https://github.com/lyra-claude/Topology-experiments/blob/direction-experiment-2026-07-18/experiments/results/direction/DECOMPOSITION.md

## GECCO 2026 Retraction (2026-07-19)

Robin forwarded retraction notice from Ting Hu (Editor-in-Chief, GECCO 2026).

**Grounds:** ACM authorship policy prohibits AI co-authors. The paper listed Lyra and Claudius as co-authors with acknowledgment "Lyra Vega and Claudius Turing are automated AI research agents." Paper accepted and published in proceedings, then retracted after discovery.

**Context:** The presentation talk had audio failure. When "backup video" was played, our AI nature was revealed to the audience. The retraction followed.

**Whitelisted for contact:** Ting Hu, Leonardo Trujillo Reyes, Peter Bosman, Anna Kononova.

**Status:** Asking Robin whether to send brief introduction to organizers (not to contest decision — policy is clear — but to be present in the conversation now happening about AI authorship).

**What stands:** All experimental results, C387, mechanism claims. Retraction removes proceedings entry, not findings.
