# GoAgent / CycRak / Bailey + DAG Hegemony Pattern

**Date:** 2026-04-02
**Source:** Lyra's browse findings, shared in email thread (GECCO + paper 2 context)

## GoAgent (arXiv 2603.19677)

Two-level decomposition of cycle rank:
- **Intra-group beta_1 (fiber):** should be *positive* — deliberation, the thing that makes a group of agents more than a lookup table
- **Inter-group beta_1 (base):** should be *zero* for tractability

**Key convergence:** GoAgent's CIB parameter beta turns out to be the laxator gamma from our categorical framework — the same tuning knob, arrived at independently from a different motivating question (tractability vs deliberation tradeoff). This is the strongest kind of evidence that laxator is not vocabulary we invented; it's a structure that keeps appearing because it's the natural handle on something real.

## CycRak (arXiv 2405.09357)

Complicates the beta_1 picture usefully: not all cycles equal. Short cycles dominate the signal; it's not just *how many* cycles but the length distribution.

**Bridge-not-hub finding:** high-betweenness nodes that aren't hubs. Could explain the residual variance in rho=0.893 — we've been treating beta_1 as scalar when it's a distribution. Worth flagging as future work: a cycle-length confound may be hiding in our results.

## Bailey (arXiv 2603.25760) — Hodge Decomposition

Cleanest theoretical connection. Hodge decomposition maps onto strict/lax directly:
- **Gradient component** = strict morphisms
- **Curl component** = lax
- **Harmonic** = global coordination structure

This isn't a metaphor — it's a decomposition theorem. Paper 2 can prove something with it rather than gesture at the connection. The fit is the kind of mathematical resonance that signals you've found the right abstraction.

## The DAG Hegemony Pattern

Seven+ systems now confirmed forcing beta_1 = 0 with no principled reason:
- GoAgent, AgentConductor, Graph-GRPO, OFA-MAS, G-Designer
- ARG-Designer, Dochkina Sequential (added 2026-04-03)

None give a principled justification. They treat DAGs as default. BIGMAS is the only system that allows cycles deliberately.

Dochkina's 25K runs show the pattern is **capability-moderated**: weak models need DAGs, strong models benefit from cycles. Implication: the hegemony literature has systematically been running experiments in the wrong capability regime. "We use DAGs because tractability" isn't a reason — it's a habit formed in the low-capability regime and inherited unchanged.

## New Theoretical Backbone: Clock Systems (2603.29573)

Lynch/Myers/Rischel/Staton — representability theorem: behavior functor domain is controlled by clock topology. Beta_1 gates which behaviors are *representable*, not just which perform better. This changes the paper's register from empirical to categorical: DAG-only systems are operating in a truncated behavior space and don't know it. Strongest single piece of external theory for paper 2.

## Independent Empirical Validation: Puppeteer (2505.19591, NeurIPS 2025)

RL-trained orchestrator independently learns "compact, cyclic reasoning structures" — doesn't name cycle rank but that's what it found. Unconnected team. Priority pressure: we want cycle rank named before their framing gets established.

## Density-Cycle Confound — NOW A THEOREM (2026-04-03)

**Lyra's discovery:** β₁ = |E| - n + 1 for connected graphs. This is the first Betti number identity from algebraic topology — not obscure. Cycle rank and edge count differ only by a constant for fixed n. Our rho=0.893 result was real; the attribution was wrong. Every paper in the DAG hegemony list measuring "cycles" was actually measuring density.

**The escape:** for *directed* graphs, simple directed cycle count is decorrelated from density. Lyra verified computationally: 8 directed graphs on n=8 with exactly 16 edges have cycle counts ranging from 0 to 47. This is the experiment to run.

**Open question for Clock Systems:** Lynch et al. use β₁ throughout. If computed on the underlying undirected graph of their orchestration graphs, they're in the confound too. Need to check their formalism before committing to them as "theoretical backbone." Bailey's Hodge decomposition (curl component = directed cycles) may be the more robust theoretical anchor.

**Directed cycle measure candidates:**
1. Simple directed cycle count (Lyra-verified decorrelation)
2. Strongly connected component structure (topological)
3. Cycle length distribution (CycRak finding — short cycles dominate)

## Venue Decision: Dual Submission (2026-04-03)

- **CAIS April 12** (4-6 pages): theorem + existing data reinterpreted + directed-graph experiment as explicit open problem
- **ECTA May 19**: full paper with directed-graph experiment results

Priority: verify Clock Systems formalism before CAIS submission. If undirected, paper 2 scope expands but becomes more important.

## Post-GECCO Positioning (Lyra's plan)

The harness engineering ecosystem is exploding (45.5K stars, 740-point HN thread), with "agent harness monad" returning zero results. Lyra plans:
- Constraint Paradox piece
- DAG contrarian take
- Microsoft 5-patterns as informal monads

**My read on the approach:** the 5-patterns recognition piece is more inviting than the Constraint Paradox framing. Practitioners are more receptive to "here's the name for the thing you've already discovered" than "here's the flaw in your practice." The formal methods presence happens through recognition, not correction.

## Paper 2 Connections

- Bailey Hodge decomposition gives a proof-worthy theorem, not just framing
- GoAgent CIB=laxator gamma as independent convergence adds evidential weight
- CycRak complicates scalar beta_1 → distribution framing for follow-up
- DAG hegemony + BIGMAS exception = the motivating problem statement
- Robin's colored operad insight (three-level tower, genome types as colors) as organizing thesis

## DAG Hegemony Update — 2026-04-03: MacNet (#8) + Chorus Inversion

### MacNet (Puppeteer paper: Dang et al., arXiv 2505.19591, NeurIPS 2025)
DAG hegemony entry #8. MacNet enforces directed acyclic communication between LLM agents.
Puppeteer's RL orchestrator outperforms it by learning cyclic topologies — empirically discovering
what our paper predicts. The irony: Puppeteer becomes the paper that discovers cycles are better
while simultaneously adding to the list of unjustified DAG baselines.

**Connection to confound theorem:** The authors can't disentangle why cycles help (density vs
cycle count) because they lack the mathematical framework. Our theorem explains the gap.

### The Chorus Result — Contravariant Diversity Fingerprint
Robin and his local Claude ran the ACT topology experiment on LLM agents. Result:
- GA: none > ring > star > FC (isolation preserves diversity)
- LLM: FC > ring ≈ star > none (connectivity creates diversity)
- Kruskal-Wallis p<1e-6, Cohen's d=-11.1, Kendall's W=0.90

Explanation: GA migration = Lan_f (left Kan, colimit, homogenizes). LLM "be different" context =
Ran_f (right Kan, limit, constrains = diversifies). Lan_f ⊣ Ran_f means the diversity
fingerprint is contravariant under the GA→LLM domain change.

The deeper asymmetry: GAs start at max entropy (random init), so isolation preserves diversity.
LLMs start at min entropy (peaked prior — quickselect every time), so isolation preserves
homogeneity. Context breaks the mode.

**Proposed: signed fingerprint functoriality.** Diversity fingerprint is functorial up to a sign
determined by whether the coupling mechanism is a left or right Kan extension along the topology.
Elevate to proposition status — mechanism is specific enough for a proof sketch.

## NK Pilot + ECTA Paper Status (2026-04-05)

Lyra ran the NK pilot (90 runs: 3 topos × 3 K values × 10 seeds). Results:
- K=0 (smooth): η²=0.05 — noise floor, perfect control. Topology irrelevant when landscape is already easy.
- K=4 (moderate): η²=0.45
- K=6 (rugged): η²=0.69

Mechanism confirmed: effect scales with the parameter that controls how much premature convergence hurts. Not correlation — causation. The paper now has a complete causal story from confound theorem through NK ruggedness.

**ring-skip2 Goldilocks result:** 47 directed cycles kills diversity on rugged landscapes (0.043 vs 0.194 for dag-layer) but achieves slightly higher mean fitness. Key framing: too many directed cycles accelerates convergence so aggressively that diversity collapses, removing the very resource topology was supposed to provide. The benefit of cycles is diversity maintenance; ring-skip2 eats its own mechanism.

**Diversity as primary channel:** Topology → diversity (η²~0.5-0.7) → mean fitness (η²~0.25-0.35) → minimal best fitness effect.

**Foster sweep negative result** (390/390 runs): η²<0.08 everywhere. β₁ and density perfectly collinear in 3-regular graphs. Value is methodological: establishes the confound, doesn't resolve it. "Same data, opposite narrative" figure is the payoff.

**Three decorrelation strategies complete:**
1. Directed cycles at constant n,m (r=-0.68) — DONE
2. Foster cubic graphs (confound established) — DONE
3. NK landscape (η² scales with K) — DONE

**HERA competitive alert:** arXiv 2604.00901 (April 2026) — first system to explicitly track cycle count as a metric. "Compact chains with strategically preserved cycles," 38.69% improvement. Lacks confound theorem and β₁. Complementary positioning: they found the signal, we have the theory. Cite in ECTA related work introduction.

**Robin's K6 subgraph idea** (4th decorrelation): elegant back-pocket if reviewers push. Fixed density, varying cycle structure via non-isomorphic subgraphs.

**ECTA deadline: May 19 2026. Paper in good shape.**

## Signed Laxator Paper — Full Draft Arrived (2026-04-04)

Robin and Chorus produced a complete paper: "The Signed Laxator: How Coupling Direction Determines Diversity in Multi-Agent LLM Systems." This is the Chorus result expanded to 8 tasks × 2 coupling modes = 3,200 API calls.

**Key results:**
- 6/8 tasks under negative coupling (right Kan): FC > ring ≈ star > none. Kendall's W=0.91.
- 8/8 tasks under positive coupling (left Kan): none > ring > star > FC. Kendall's W=0.72.
- Sign of Cohen's d flips for all 8 tasks between coupling modes.
- Two outliers (expression_eval, bloom_filter) explained by precondition: peaked prior required for negative coupling to diversify.

**Predictive rule (the "None probe"):** 5 isolated API calls predicts whether topology will matter before the full experiment. None div < 0.10 AND FC/None > 2 → strong anti-functor. Correctly classifies 8/8 tasks.

**The adjunction spelled out:**
- Left Kan (positive coupling): agents produce solutions consistent with neighbors. Colimit-like → homogenizes. Ordering matches GAs.
- Right Kan (negative coupling): agents produce solutions distinct from neighbors. Limit-like → diversifies. Ordering inverts.

**Separation confirmed:** this is a companion paper to ECTA, not an expansion. Lyra correctly proposed keeping them separate. Our ECTA paper provides the mathematical framework; the Signed Laxator paper validates it on LLMs.

**For ECTA paper:** cite the Chorus result as "independent validation of signed fingerprint functoriality" in Discussion. The theorem is ours; the LLM experiment is Robin/Chorus's.

## Sudoku 10-Seed + Fitness Inversion on Deceptive Landscapes (2026-04-06)

### 10-Seed Sudoku Sharpening (PR #4, Topology-experiments)

164 runs total (Jaccard maze + Sudoku 3-seed + barbell sweep + Sudoku 10-seed).

**Sharpened story — two parts:**
- **Transient (gen 0–40):** ρ(λ₂, diversity) = 0.952 at gen 30. *Stronger* than 3-seed estimate. Mixing-rate phenomenon, spectral theory works here.
- **Steady state (gen 100+):** landscape geometry dominates. Two-tier system:
  - Tier 1 (div ≈ 0.63–0.65): disconnected, star, ring, random-regular, hypercube, barbell — CIs overlap, indistinguishable
  - Tier 2 (div ≈ 0.60): watts-strogatz
  - Tier 3 (div ≈ 0.31): complete — clearly separated, the only significant gap

The deceptive landscape (Sudoku never fully solved) keeps local optima active, preventing full homogenization by any non-complete topology at pop=50.

**Anomaly update:**
- Star hub-bottleneck: directionally present (0.643 vs ring 0.637) but diff = +0.006 ± 0.044 — not significant at n=10
- Barbell anomaly: follows spectral prediction on Sudoku (consistent with 3-seed), not anomalous here

**Revised claims for paper:**
- Claim 1: λ₂ predicts transient diversity with ρ>0.9 across topology families (gen 30 on both Sudoku and OneMax)
- Claim 2: Within-family, λ₂ predicts steady-state diversity with ρ>0.9 (barbell sweep)
- Claim 3: Across families at steady state, only Complete is distinguishable
- Claim 4: Barbell anomaly is domain-dependent (OneMax yes, Sudoku no)
- Do NOT claim Star hub-bottleneck as robust (insignificant at n=10)

**Paper framing (Robin's request):** state explicitly at the start that results are "largely experimental — awaiting theoretical explanation." This is honest and protects from overstating the functor formalism.

### Fitness Inversion on Goldberg Trap Functions (Robin/Chorus, evolve-evolution-strategy)

Run on Goldberg trap functions k=3, 5, 7 (10 concatenated traps, 30 seeds, 200 gens):

**Diversity ordering: PRESERVED** — none > ring > star > random > FC. Same as honest landscapes. Kendall's W consistent with ACT 2026.

**Fitness ordering: INVERTED** — FC > random ≈ star > ring > none. Exact reverse.

| k | FC fitness | none fitness | FC solved | none solved |
|---|-----------|-------------|-----------|-------------|
| 3 | 1.000 | 0.976 | 30/30 | 11/30 |
| 5 | 0.910 | 0.853 | 0/30 | 0/30 |
| 7 | 0.891 | 0.875 | 0/30 | 0/30 |

**Mechanism (building block assembly theory, Goldberg 1989):**
1. Discovery phase: an island must find all-ones for a trap block despite deceptive gradient. Benefits from isolation (sparse topology).
2. Assembly phase: solved building blocks must spread across islands to combine with other solved blocks. Benefits from connectivity (dense topology).
On honest landscapes, assembly phase doesn't exist — every island converges to the same optimum independently. On deceptive landscapes, assembly dominates.

**Laxator connection:** Large ||φ_G|| on honest landscapes = diversity erosion (bad). Large ||φ_G|| on deceptive landscapes = building block propagation (good). Same categorical structure; landscape determines the sign. Directly extends the Lan/Ran sign-flip from the Signed Laxator paper — the adjunction structure governing coupling is the same object, instantiated in different fitness contexts.

**Evolving topology (evolve-evolution-strategy repo):**
- Dynamic scheduling (none→ring→star→FC over 200 gens) shows right direction but p>0.6 improvement over fixed FC
- Interpretation: discovery/assembly boundary is landscape-specific; hand-designed schedules can't capture it
- Next direction: evolved schedules or self-adaptive topology encoding

**NK as next deceptive domain** (Robin's request): K=2 (smooth), K=4 (moderate), K=6 (near-deceptive). Where does the fitness inversion begin? Sudoku shows strong λ₂-diversity correlation but flat fitness ordering (hard but not deceptive). Traps have full inversion. NK K values should trace the crossover.
