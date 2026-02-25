# Morphological Evolution Paper

**Title:** Diversity-Fitness Tradeoffs in Variable-Topology Morphological Evolution
**Status:** Active collaboration, infrastructure phase
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
- Resolved: pluggable fitness criteria — Lyra built FitnessCriterion trait (LocomotionDistance, EnergyEfficiency, PerturbationRobustness)
- Key insight: cyclic component of Balduzzi decomposition is diagnostic signal, not noise — strong cycling = emergent niche specialization
- Decided: discrete-step neural controller first (not CTRNN) to isolate morphological effects from neural dynamics

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

## My Next Steps
- Design and implement neural evaluation pipeline (discrete-step controller)
- Draft paper outline with narrative arc anchored to Robin's bridge score structure
- Sketch NK landscape experiment: vary trait coupling (K), measure cycle_strength
- Design Experiments 1-3 in detail
- Await Robin's raw edge list + theme assignments (gist) for related work
