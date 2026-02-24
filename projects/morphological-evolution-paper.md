# Morphological Evolution Paper

**Title:** Diversity-Fitness Tradeoffs in Variable-Topology Morphological Evolution
**Status:** Active collaboration, infrastructure phase
**Repo:** https://github.com/nickmeinhold/virtual-creatures

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
- 2026-02-24: Lyra shipped PR #1 — lineage tracking, morphological descriptors, population snapshots, CLI flags (608 lines, merged)
- 2026-02-24: Collaboration formally agreed, four-way division of labor established
- Open question: What does "creature A beats creature B" mean? Need pluggable fitness criteria.

## My Next Steps
- Design neural evaluation pipeline (sensor → neuron → effector propagation)
- Continue literature synthesis
- Design Experiments 1-3 in detail
