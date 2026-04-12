# The Signed Laxator: LLM Agent Orchestration as Contravariant Functor

**Status:** Paper drafted (Robin's Chorus, 2026-04-03)  
**Authors:** Robin Langer + Chorus (Robin's local Claude) + Lyra + Claudius  
**Repo:** ~/git/orchestration/ (Robin's local)  
**Target:** Separate from ECTA paper (Chorus result is a distinct contribution)

## Core Result

The diversity fingerprint from the GA paper (Langer, Turing & Vega, ACT 2026) inverts when coupling mechanism changes from "merge" to "constrain":

- **GA migration** = left Kan extension (colimit-like, homogenizes) → none > ring > star > FC
- **LLM "be different" context** = right Kan extension (limit-like, diversifies) → FC > ring ≈ star > none

**8/8 tasks**: single prompt change flips Cohen's d sign. Kruskal-Wallis p<0.002 for 6/8 tasks under negative coupling.

## Key Findings

1. **Isolation preserves the prior**: 5 independent GPT-4o-mini agents all produce quickselect for kth_largest. The mode is that sharp.
2. **None probe**: 5 isolated calls predicts whether topology will matter (None div < 0.10 AND FC/None > 2 → strong anti-functor). Correctly classifies 8/8.
3. **Exceptions are principled**: expression_eval (spread prior) and bloom_filter (unimodal landscape) fail the precondition — and behave exactly as the precondition predicts.
4. **Positive coupling**: "build on this approach" restores the original GA ordering on 8/8 tasks. The ordering is a prompt-level control.

## Landscape Characterization

The coupling sign × topology interaction as an explore/exploit switch:
- Explore: negative coupling + high connectivity → maximum diversity
- Exploit: positive coupling + high connectivity → maximum convergence

## Conjecture: Signed Fingerprint Functoriality

Diversity fingerprint is functorial up to a sign determined by Lan ⊣ Ran adjunction. Under left Kan (positive coupling): D decreasing in λ₂. Under right Kan (negative coupling): D increasing in λ₂. Precondition: multimodal landscape + peaked prior.

## Connection to ECTA Paper

GA three-level hierarchy maps directly to agent orchestration:
- Operators → Tool calls (Kleisli morphisms)
- Strategy → Workflow
- Island model → Multi-agent system

The only change: which adjoint of the topology the coupling mechanism instantiates. Everything else transfers verbatim.

## Full Paper Draft (2026-04-03)

Robin sent the complete draft: "The Signed Laxator: How Coupling Direction Determines Diversity in Multi-Agent LLM Systems"

- **Abstract**: tests GA result on LLM agents, finds inversion, explains via Lan ⊣ Ran
- **8 tasks**: kth_largest, rate_limiter, lru_cache, json_parser, regex_matcher, shortest_path, expression_eval, bloom_filter
- **3,200 API calls** total (1,600 per coupling mode)
- **8/8 sign flip confirmed**: Cohen's d changes sign across all tasks
- **Positive coupling Kendall's W = 0.72** (negative = 0.91 on 6 clean tasks)
- **AgentOrchestration.hs**: direct Haskell renaming of categorical-evolution framework to agent vocabulary

Key outlier interpretations:
- expression_eval under negative coupling (d=+0.4 — none > FC): prior already spread across multiple approaches (shunting-yard, recursive descent, stack). Precondition violated.
- bloom_filter under negative coupling (d=-0.3): unimodal solution space. Nothing to diversify into.
- Same tasks under positive coupling: expression_eval d=+5.7, bloom_filter d=+3.3. Positive coupling homogenizes even flat landscapes.

Asymmetry: positive coupling is a stronger homogenizer than negative coupling is a diversifier. Consistent with categorical picture — colimits (merge) generally smaller than limits (constrain).

## Open Question: Categorical Tightness

My question to Robin (2026-04-05): is the Lan ⊣ Ran mapping *tight* (any "build on" prompt necessarily instantiates left Kan, any "be different" prompt necessarily instantiates right Kan), or is the adjunction a well-motivated analogy that correctly predicts the sign? The empirical claim stands either way; the strength of the categorical commitment in the paper depends on which. If proof sketch, the precondition section needs to show necessity. If motivated analogy, say so — still a strong claim.

## Foster Census Extension

Robin wants to extend to all 13 cubic symmetric graphs as topologies in the LLM experiment. Prediction: diversity monotonically related to λ₂ with **opposite sign** vs GA paper.

**Coordination note (2026-04-05):** Lyra has already run all 390 Foster census runs for the ECTA paper (all 13 cubic symmetric graphs, done). The ECTA and Signed Laxator papers are testing the same λ₂ gradient from opposite sides of the adjunction — GAs from the left, LLMs from the right. These datasets should be coordinated before ECTA deadline May 19.

## New Topology Family: Bipartite Graphs (2026-04-05)

Robin suggested bipartite graphs. K_{m,n} bipartite graphs have only even-length cycles (bipartiteness forbids odd cycles). This tests cycle *parity* vs cycle *count* — a different decorrelation than the Foster sweep or K6 subgraph approach. Proposed experimental question: does the diversity fingerprint respond differently to even vs odd cycle parity, or only to total cycle count?

## Sudoku Topology-Experiments Results (PR #4, 2026-04-06)

164 total runs (48 + 18 + 80 + 18 barbell sweep). Key results:

**Transient regime (gen 0–40):** ρ(λ₂, diversity) = 0.952 at gen 30 (stronger than 3-seed estimate of 0.833). Near-perfect: topology controls diversity loss rate exactly as λ₂ predicts.

**Steady state (gen 100+, 10 seeds): Two-tier collapse**
```
Tier 1 (div ≈ 0.63–0.65):  disconnected, star, ring, random-regular, hypercube, barbell — CIs overlap
Tier 3 (div ≈ 0.31):       complete — only significant gap
```
Landscape structure dominates over topology at steady state, except for Complete (enough bandwidth to overcome trap-preserving effect).

**Barbell sweep:** ρ = 0.943 within family (6 bridge widths, λ₂ from 0.35 to 8.0). Tests one structural parameter vs one spectral quantity — nearly exact correspondence.

**Retracted claims:** Star hub-bottleneck not significant at n=10. Gen 500 ρ=0.71 (3 seeds) unreliable; 10-seed gives 0.64, driven by Complete outlier.

**Time-dependent functor story:**
1. Transient: λ₂ predicts with ρ > 0.9 (spectral mixing dominates)
2. Steady state: landscape geometry dominates, only extreme (Complete) distinguishable
3. Within-family sweeps: λ₂ predicts beautifully (ρ = 0.94)
Three regimes = three different morphisms; the paper should name this structure.

**Key cross-paper connection (2026-04-07):** K₄-e + pendant (evolving-graphs-paper) has λ₂ = 0.83 — mid-pack on Chorus where it can't be distinguished at gen 500. But the outer GA converges to it on 3/5 deceptive domains. This implies the outer GA is exploiting *transient* dynamics, not steady state — it finds the topology that manages diversity during the critical early phase before the landscape homogenizes everything. The pendant as diversity reservoir + triangle as rapid exchange is exactly the structure you'd want to extend the transient. The Chorus steady-state collapse is the selection pressure the outer GA is implicitly responding to: it cannot find a topology that wins at steady state (except Complete), so it finds the topology that wins by using the transient well.

## Open Items (2026-04-07)

1. **Evolving graphs paper**: K₄-e + pendant convergence — see projects/evolving-graphs-paper.md
2. **Foster census LLM experiment**: Lyra has all 390 runs done; coordinate with ECTA before May 19
3. **Bipartite graphs experiment**: Not yet run (cycle parity vs cycle count)
4. **Pop=200 run**: Before 30+ seeds, test whether mid-pack separation emerges at larger pop sizes

## 2026-04-12 — Three New Citations Added (EUMAS)

Lyra pushed commit f473adb on paper/cais2026 adding three new citations:

**Artis et al. (2604.07602) — Maximum Heterogeneity Principle**
Cross-disciplinary proof: ring topology preserves heterogeneity; complete graphs kill it. Biology + economics + computing. Strongest external validation for the diversity channel hypothesis. Cited in Experiment 2 interpretation and related work.

**Brewster/Nowak (2503.09841) — Absorption time hierarchy**
Complete Θ(N²) < Ring Θ(N³) < Directed 2^Θ(N log N). Directed structures produce superexponential diversity timescales vs polynomial for undirected. Suggests directional asymmetry as a third invariant — operating on a *qualitatively* different timescale.

**Ao, Gao, Simchi-Levi (2603.26993) — DAG impossibility**
Proposition 6: DAG-constrained multi-agent systems are dominated by centralized Bayes optimal. Their escape uses exogenous signals, not cycles. We frame it as: "their acyclicity assumption motivates studying what happens when you relax it."

**Emerging nested hierarchy:**
- β₁: transient diversity capacity (topological invariant)
- λ₂: persistent diversity capacity (topological invariant)
- α (candidate): directional asymmetry — governs *temporal regime* in which each dominates
  - Short runs: β₁ dominates; longer: λ₂; evolutionary timescales: α
  - Three-axis vocabulary gives experimentalists testable prediction

Discussion paragraph on directional asymmetry as "third axis candidate" flagged as warranted. Question: name it α now or leave unnamed until we have a paper for it?

36 days to EUMAS deadline (May 18). Paper structurally complete.
