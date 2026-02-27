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

## Key Insight for Paper
The Balduzzi transitive-cyclic decomposition appears **nowhere** in the graph. No formal theory connects diversity maintenance to fitness landscape structure in variable-topology spaces. The empirical engineering of diversity (10+ MAP-Elites variants) far outstrips theoretical understanding of *when and why* it matters. This is our paper's contribution in one sentence.

## Full Edge List Received (2026-02-27)
Robin sent the complete D3.js visualization HTML. All 503 nodes and 446 edges now parsed. Confirms structural hole analysis and gives full edge-type distribution (uses, extends, is_variant_of, outperforms, related_to, evaluated_on, combined_with, generalizes, inspired_by).

## Query Results

### Query 1: NEAT + Body Co-Optimization + Credit Assignment (ANSWERED)
Robin returned detailed synthesis from 3 meta-summaries and ~8 concept summaries.

**Key work:** ViE-NEAT (Zardini et al. 2021, arXiv:2104.12175) — dual-population: morphology via Viability Evolution, controllers via NEAT with full topological mutation + speciation. Random pairing creates co-evolutionary dynamic.

**Three credit assignment strategies in literature:**
1. **Dual-population separation** (ViE-NEAT, DM-ME) — separate archives/populations, joint evaluation. Pragmatic, not principled.
2. **Modular controllers** (Mertan & Cheney 2023, arXiv:2306.09358) — decentralized control, each module semi-independent. 95% fitness at 1380 gen vs 1787 for global controllers. Implicit fix: brain ≈ invariant under morphological mutation, so fitness changes attributable to body.
3. **Shared CPPN encoding** (Auerbach & Bongard 2011) — single CPPN generates both body and controller. Trades credit assignment for encoding constraint on joint space.

**Critical negative result:** Mertan & Cheney (2024, arXiv:2402.09231) — naive co-optimization → premature convergence. Morphology gets trapped early because controller can't keep up with morphological innovation. Regions discoverable by separate optimization become inaccessible under joint search.

**Key gap identified:** Nobody uses NEAT's speciation mechanism as a cross-boundary credit assignment tool. Speciation protects neural topological innovation — same principle could protect morphological innovation by giving new body plans a niche where controllers can adapt before facing competition. This is speciation-as-credit-assignment.

### Query 2: Diversity-Fitness in Variable-Dimensional QD (PENDING)
### Query 3: OEE-Neuroevolution Connection (PENDING)

## Available Resources
Robin offers to run queries against both:
- **Level 1 vector DB:** Paper-level search
- **Level 2 vector DB:** Concept-summary-level search
