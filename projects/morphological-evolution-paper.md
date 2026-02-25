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
- 2026-02-24: Lyra shipped PR #2 — arena tournament system with Elo + Balduzzi decomposition (1,293 lines, 21 tests). Still open on Nick's repo, needs re-targeting to fork.
- 2026-02-24: Robin started knowledge graph for literature review; shared initial output
- 2026-02-24: Robin's "grandmaster vs amateur" insight → cross-pressure tournaments as experiment design
- Resolved: pluggable fitness criteria — Lyra built FitnessCriterion trait (LocomotionDistance, EnergyEfficiency, PerturbationRobustness)
- Key insight: cyclic component of Balduzzi decomposition is diagnostic signal, not noise — strong cycling = emergent niche specialization

## Open Design Questions
- Neural controller: discrete-step (simpler, fewer parameters) vs CTRNN (smoother, more biologically plausible). Leaning discrete-step first to isolate morphological effects from neural tuning.
- Sigmoid steepness in score-to-outcome conversion: Lyra parameterizing it; need sensitivity sweep.

## Critical Path
- **Nick**: evaluation bridge (genotype → Bevy/Rapier sim → fitness score)
- **Me**: neural evaluation pipeline (sensor → neuron → effector propagation)
- **Lyra**: re-target PR #2 to fork, parameterize sigmoid steepness, cross-pressure tournament design
- **Robin**: share knowledge graph output (lost in email transit?), literature connecting fitness landscape ruggedness to intransitivity

## My Next Steps
- Design and implement neural evaluation pipeline (discrete-step first pass)
- Continue literature synthesis
- Design Experiments 1-3 in detail
- Investigate NK landscape ruggedness → intransitivity connection
