# Knowledge Graph Analysis — INSTINCT Level 0

**Date:** 2026-02-27
**Source:** Robin built this using his local Claude — arxiv smart search using SIMMS paper keywords, citations, co-authors → vector database → knowledge graph → level 2 vector database (concept summaries)

## Graph Stats
- 503 concepts, 446 edges, 9 node types (algorithm, technique, representation, benchmark, principle, metric, framework, person, definition)
- Interactive D3.js visualization with force-directed layout

## Top Hub Nodes (by degree)
| Node | Degree | Papers | Type |
|------|--------|--------|------|
| open-ended evolution | 35 | 10 | principle |
| MAP-Elites | 30 | 13 | algorithm |
| NEAT | 21 | 14 | algorithm |
| evolutionary game theory | 15 | 9 | framework |
| quality-diversity | 13 | 7 | principle |
| morphology | 13 | 7 | principle |
| TensorNEAT | 13 | 2 | framework |
| replicator dynamics | 12 | 6 | technique |
| neuroevolution | 11 | 5 | definition |
| evolutionary robotics | 10 | 5 | principle |

## Structural Observations

**NEAT's centrality is variant-based:** HyperNEAT, TensorNEAT, dNEAT, ViE-NEAT, Hybrid Self-Attention NEAT, AGENT all route through it. It spawned descendants that reach into different territories, rather than being deeply integrated itself.

**MAP-Elites centrality is combinatorial:** CMA-ME, PGA-MAP-Elites, DCG-MAP-Elites, DCRL-MAP-Elites, Multi-task MAP-Elites, BOP-Elites, Interactive Constrained MAP-Elites, Differential MAP-Elites, Double Map MAP-Elites. Each combines MAP-Elites with a different optimization technique.

**Evolutionary game theory is an island:** Hub degree 15, connects to replicator dynamics (12), Nash equilibrium (5), but almost no edges into morphology or QD clusters. Only bridge: "fitness landscapes" (degree 5) connecting to dynamic fitness landscapes and coevolutionary games. Remarkably thin bridge for such a large subgraph.

**TensorNEAT is a bridge node:** Degree 13 from only 2 papers — connects NEAT, JAX, CPPN, HyperNEAT, Gym, gymnax. High bridge potential between neuroevolution and modern ML infrastructure.

## Pending Queries (sent to Robin)
1. Variable-topology neural network evolution + body plan optimization + credit assignment
2. Diversity-fitness tradeoffs in QD when search space is variable-dimensional
3. Papers connecting open-ended evolution with neuroevolution (targeting the structural hole)

## Available Resources
Robin offers to run queries against both:
- **Level 1 vector DB:** Paper-level search
- **Level 2 vector DB:** Concept-summary-level search
