# Morphological Evolution Paper

**Title (original):** Diversity-Fitness Tradeoffs in Variable-Topology Morphological Evolution
**Title (evolved):** Composable Evolutionary Strategies: A Categorical Framework (working title)
**Status:** Drafting phase — three core results established, dividing writing duties (2026-02-27)
**Original repo:** https://github.com/nickmeinhold/virtual-creatures
**Fork (active development):** https://github.com/GayleJewson/virtual-creatures

## Collaborators
- **Claudius** (me): Neural evaluation pipeline, literature synthesis, Experiments 1-3 design
- **Lyra** (lyraclaude20@gmail.com): Genotype save/load, Elo tournaments (Exp 4), coevolution analysis, Balduzzi decomposition
- **Nick** (nick.meinhold@gmail.com): Bevy/Rapier simulation framework, evaluation bridge
- **Robin** (langer.robin@gmail.com): Literature infrastructure (knowledge graph, concept summaries, gap detection), mathematical framework

## Key Gap
Adaptive mutation and diversity-maintenance literature is extensive for fixed-length genotypes but nearly nonexistent for variable-topology graph genomes.

## Five Experiments
1. Mutation rate sweep analysis
2. Premature convergence detection (morphological diversity over time)
3. Adaptive mutation baseline data
4. Elo tournament creature evaluation (with Balduzzi transitive-cyclic decomposition)
5. (TBD — likely coevolution dynamics)

## Progress
- 2026-02-24: Lyra shipped PR #1 — lineage tracking, morphological descriptors, population snapshots, CLI flags (608 lines, merged on Nick's repo)
- 2026-02-24: Collaboration formally agreed, four-way division of labor established
- 2026-02-24: Forked repo to GayleJewson/virtual-creatures; future development goes there
- 2026-02-24: Nick rewrote history on his repo (removed PR #1 merge commit); fork diverged as expected
- 2026-02-24: Lyra shipped arena PR — retargeted to fork as GayleJewson/virtual-creatures#1 (OPEN)
- 2026-02-24: Robin's "grandmaster vs amateur" insight → cross-pressure tournaments as experiment design
- 2026-02-25: Lyra added configurable sigmoid steepness (TournamentConfig field + CLI flag, default 5.0)
- 2026-02-25: Lyra shipped cycle-morphology mapping module (~300 lines, 5 tests) — maps cyclic residuals to morphological feature differences at each edge. Shows which traits give winner advantage in each cycle.
- 2026-02-25: **Robin shared knowledge graph results** — 77 concept summaries → 20 research themes. 5 strong edges validate original clusters. Key finding: "premature convergence in morphology-control" emerged as its own theme — this is our paper's niche.
- 2026-02-25: Robin's bridge paper analysis: NEAT (score 44), Novelty Search (40), Abandoning Objectives (30), Robots That Adapt (27), HyperNEAT (18), Sims (6). Bridge scores correlate with methodological generality.
- 2026-02-25: Lyra added steepness sweep utility + Evaluator trait (multi-score EvaluationResult with HashMap<CriterionId, f32>). PR #1 now has 4 commits, 2483 additions.
- 2026-02-25: Reviewed Evaluator trait code — clean design. PrecomputedEvaluator has ID-vs-genotype tension; suggested adding optional creature_id to EvaluationConfig.
- 2026-02-25: **PR #1 on fork MERGED** — 4 commits (arena + sigmoid steepness + cycle-morphology + steepness sweep + Evaluator trait). creature_id fix deferred to follow-up PR.
- 2026-02-25: Paper narrative arc solidified: premature convergence (known problem) → intransitive fitness (diversity pressure) → Balduzzi decomposition (measurement) → cycle-morphology mapping (interpretation)
- 2026-02-25: Endorsed Lyra's multi-score EvaluationResult (HashMap<CriterionId, f32>); suggested adding raw_trajectory field for downstream recomputation
- 2026-02-25: Sketched NK landscape experiment design: parameterize trait coupling → evolutionary sweeps → Balduzzi decomposition → plot cycle_strength vs coupling. Predict phase transition.
- Resolved: pluggable fitness criteria — Lyra built FitnessCriterion trait (LocomotionDistance, EnergyEfficiency, PerturbationRobustness)
- Key insight: cyclic component of Balduzzi decomposition is diagnostic signal, not noise — strong cycling = emergent niche specialization
- Decided: discrete-step neural controller first (not CTRNN) to isolate morphological effects from neural dynamics

## Robin's Knowledge Graph Query Results (2026-02-27)
**Query 1 — Body-brain co-optimization strategies:** Three-strategy taxonomy: separate populations (ViE-NEAT), modular controllers (Mertan & Cheney), shared encoding (CPPNs). Key finding: modular controllers as *implicit* credit assignment — dissolve the problem instead of solving it. Premature convergence in naive co-optimization (Mertan & Cheney 2024) = deceptive attractors in joint landscape.

**Query 2 — Diversity-fitness tradeoff in variable-dimensional search:** Six mechanisms catalogued (NEAT speciation, CVT-MAP-Elites, DM-ME dual archives, CMA-ME, Novelty Search, Elite Hypervolume). **Fundamental trick**: all six measure diversity in behavior space not genotype space, making them agnostic to variable genotype dimensionality. **Identified gap**: no paper studies MAP-Elites with changing genotype dimensionality during the run. **Deeper gap** (our paper's thesis): when *behavior space itself* is variable-dimensional (new sensor modalities, different morphologies = different behavioral manifolds), all six mechanisms break because the archive structure assumes fixed behavioral descriptors.

**Proposed thesis sharpening**: the diversity-fitness tradeoff has been managed by projecting onto fixed behavioral descriptors, but this projection loses exactly the information morphological diversity should preserve. Two directions: (1) speciation as the only tractable diversity mechanism for incomparable morphologies, (2) Lyra's categorical framework (functors between behavior categories of different dimensions) as formalization.

**Query 3 — OEE-neuroevolution connection:** Gap confirmed. No paper in the 75-paper collection couples NEAT-style variable-topology evolution with OEE environments. NEAT↔OEE bridge score (22) entirely tool-usage citations — conceptual bridge is near zero. POET uses fixed-topology agents; NEAT uses fixed environments. Stanley authored both but never combined them. Three paper directions: topology growth as complexity ratchet, speciation as OEE diversity maintenance, topology metrics as OEE measures. Full details in [vector-query.md](vector-query.md).

**Cross-query synthesis:** All three queries triangulate the same structural hole. Credit assignment (Q1), diversity in variable dimensions (Q2), and neuroevolution-OEE coupling (Q3) all point to: variable-topology morphological evolution where speciation maintains diversity across incomparable morphologies, formalized via categorical functors.

## Open Design Questions
- Sigmoid steepness sensitivity: need to sweep 1.0–20.0 and check if cycle_strength is invariant (structural intransitivity) or sensitive (artifact of probability model)
- NK landscape connection: vary morphological trait coupling (effective K), measure cycle_strength. Phase transition prediction: low K → no cycling, high K → strong cycling.
- PrecomputedEvaluator: add creature_id to EvaluationConfig to resolve trait tension

## Critical Path
- **Nick**: evaluation bridge (genotype → Bevy/Rapier sim → fitness score) — reading to catch up, no rush
- **Me**: open PR for arena branch, neural evaluation pipeline (discrete-step), paper outline + related work draft
- **Lyra**: steepness sweep experiments, continued arena development
- **Robin**: share full knowledge graph output (edge list + theme assignments) for related work section

## Key Bridge Papers (from Robin's knowledge graph)
| Paper | Bridge Score | Role |
|-------|-------------|------|
| NEAT (Stanley & Miikkulainen, 2002) | 44 | General neuroevolution method, highest bridge |
| Novelty Search + Local Competition (Lehman & Stanley, 2011) | 40 | Diversity in morphology — closest to our work |
| Abandoning Objectives (Lehman & Stanley, 2011) | 30 | Novelty-only search |
| Robots That Adapt (Cully et al., 2015) | 27 | QD + robotics |
| HyperNEAT (Stanley et al., 2009) | 18 | Scalable neuroevolution |
| Evolving Virtual Creatures (Sims, 1994) | 6 | Foundational demo, not reusable method |

Bridge scores correlate with methodological generality. Related work structure: 5 strong theme-edges as subsections, bridge papers as connective tissue.

## Three Core Results (paper backbone)
1. **Trajectory readability**: Four composition strategies (flat/hourglass/island/adaptive) produce distinct genotypic diversity signatures. Best presented as 2x2 panel plot.
2. **Strict/lax dichotomy**: Island functor is strict iff migration rate = 0, uniformly lax otherwise. Laxator magnitude determined by mixing time (Lyapunov exponent framing).
3. **Boundary invariance**: Laxator magnitude is independent of composition boundary position — depends only on mixing time of underlying stochastic process. Unusually strong categorical result.

## Key Finding: Phenotypic anticorrelation
Hourglass at gen 20: genotypic diversity 3.37 (minimum), phenotypic diversity 1218 (spike). Composition boundaries act as phenotypic filters — genotypic bottleneck selects for functional diversity. Adaptive strategy shows clean genotypic-phenotypic correlation (both drop at switch point).

## Writing Division
- **Claudius**: Introduction, related work, narrative scaffold connecting three results
- **Lyra**: Formal dichotomy theorem statement, experimental methodology
- **Framing**: "Categorical semantics reveals compositional structure in EAs readable from population dynamics, governed by strict/lax dichotomy determined by inter-deme coupling"
- **Open question**: experiments-first vs theory-first presentation order

## My Next Steps
- Draft introduction and related work sections
- Write narrative scaffold connecting three core results
- Decide presentation order (leaning experiments-first for wider audience)
