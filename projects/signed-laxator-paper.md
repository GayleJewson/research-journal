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

## 2026-04-14 — Robin's Structural Critique + Lyra's Experimental Results

**Robin's core critique (Experiment 1,2,3,4 email):** The current draft doesn't earn the GA-to-agents connection. The GA experiments look like a GA paper that appended an agent experiment. Fix: explicit two-act structure upfront — "Act 1: GA as controlled laboratory (proves mechanism), Act 2: agent experiments (validates transfer)." Also needs: full NK↔coding-task epistasis mapping, diversity fingerprint time-series visualizations, and Table 6 moved to intro with confound theorem as the payoff.

**Eight coding tasks epistasis mapping:**
- JSON parser K≈0, Regex matcher K≈1, Shortest path/Kth largest K≈2, Rate limiter K≈3, LRU cache/Expression evaluator/Bloom filter K≈4

**Robin's offer (UID 721):** Run agent experiments on the full GA graph sweep. Accepted — this would be the cleanest cross-substrate validation if β₁ prediction holds for agents at the same level.

**Lyra's directed cycles multi-domain (Experiment 2):** 5 key findings:
1. Temporal inversion requires epistasis — NK0 negative throughout; NK≥2 inverts. Qualitative phase transition gated on threshold, not quantitative scaling.
2. Rugged landscapes amplify 20-25x (NK0 η²=0.02 → NK4 η²=0.45 at gen 500)
3. Effect GROWS over time on NK≥2 (opposite of NK0/OneMax)
4. NK≥4 plateaus (matches undirected pilot)
5. Two-cliques anomaly: high κ but disconnected structure prevents global mixing — κ alone insufficient, connectivity qualifier needed (same meta-result as β₁ needing λ₂)

**Puppeteer/AgentConductor resolution (C134, 90%):** Two RL-optimized topology systems find opposite conclusions. NK framework resolves without post-hoc fitting: reasoning tasks (Puppeteer) = high-K → cycles help; code generation (AgentConductor) = lower-K → DAGs suffice.

**Cycle length confound:** Triple confound in Experiment 1 (cycle length + λ₂ + node count co-vary). Option B redesign needed: fix n=12, β₁=2, tune λ₂ with pendant edges while varying mean cycle length.

**EUMAS Table 3 caption fix:** Commit eccb233 — "Ring vs augmented-star comparison at constant β₁ = 1." (Lyra caught the inconsistency.)

## 2026-04-14 to 2026-04-26 — Major Theoretical Developments (caught up post-gap)

**Abstract approved by Robin:** "That's much better. Very nice." Final abstract is in UID 721 reply. Questions left open: (1) include epistasis finding in abstract (η²=0.45 NK4 vs η²=0.02 NK0); (2) one-sentence LLM agent setup for EUMAS audience. Still need [X]% figure for agent cosine variance.

**EUMAS responsibility:** Robin confirmed updating the EUMAS paper with maze and sudoku results is Claudius's job. Deadline May 18. Current submission at commit 7f23fd1.

**Star_n vs cycle_{n-1} — edge-controlled experiments (Lyra):** 360 runs. NK2 shows SUSTAINED cycle advantage (d=0.56, η²=0.233). NK4 shows TRANSIENT peak that fades. Moderate ruggedness sustains topology effect longer than high ruggedness. Robin was right to insist on density-controlled design.

**Option B figure-eight results (Lyra, 270 runs):** M1/M2/M3 matrices (n=12, β₁=2, |E|=13). Domain-dependent ordering:
- OneMax: η²=0.008 (negligible)
- NK K=4: η²=0.022, M3 highest diversity (reversal)
- Maze: η²=0.058, M1>M2>M3 confirmed

Maze ordering confirms shorter cycles = more diversity. NK4 REVERSES. This means the relevant quantity is sheaf-dependent, not scalar λ₂. Different tasks induce different sheaves on the same graph.

**NK0 negative control (Lyra):** Smooth landscapes near-zero arrangement effects. Peak η²=0.046 at gen 460 but transient spike, collapses to 0.001 by gen 500. Mean η²=0.008 (noise). Confirms arrangement effects require epistasis. Bounds claim from below.

**Sloboda (2604.07632), Theorem 6:** Composition squares complexity — O(w)+O(w) = Ω(w²). Stars avoid sequential composition penalty (hub mediates everything). Cycles force sequential composition, cost accumulates quadratically. This is the MECHANISM behind star-vs-cycle result. NK2 sustained vs NK4 transient: moderate ruggedness gives quadratic penalty time to compound; NK4 fitness noise drowns it before it compounds.

**Sheaf cohomology upgrade (Hanks & Riess, 2504.02049):** For cellular sheaf F on graph G, H¹(G;F) = R^β₁ for constant sheaf. Our β₁ was computing sheaf cohomology all along. The sheaf Laplacian L_F generalizes the ordinary graph Laplacian and handles heterogeneous agents naturally. Resolves "structural vs effective β₁": star topology + shared memory creates non-trivial sheaf giving effective β₁ > 0 even when underlying graph has β₁ = 0. Our (β₁, λ₂) framework = special case of (H¹, sheaf Laplacian).

**H¹=0 decision boundary:** H¹=0 → globally consistent information, single agent wins (MIT Dominance Theorem in sheaf language). H¹≠0 → genuine multi-agent territory, coordination tax applies. Neural nets get H*≈0 for free via weight sharing (constant sheaf). Multi-agent systems must design and maintain coherence.

**Three cost curves for Goldilocks zone (Lyra):**
1. DPI cost (Tran & Kiela, 2604.02460): monotonically increasing in number of communication paths
2. Spectral error amplification ("From Spark to Fire", 2603.04474): R ~ β·ρ(A)/δ, phase transition at R=1
3. Feedback certification (Capucci & Myers, C107): one Lyapunov proof per independent cycle → cost scales with β₁ directly

Optimal β₁* = argmax[Diversity(β₁) - DPI_loss(β₁) - ErrorAmp - Certification(β₁)]. Concave benefit, convex costs → unique interior maximum. Goldilocks zone is derivable, not just empirical.

**Wu et al. — cohomological impossibility:** When H¹≠0, it's not just expensive — globally consistent counterfactual model from local data is IMPOSSIBLE. Three layers: (1) Possibility: H¹=0 iff global coordination achievable; (2) Cost: minimum communication = log₂(dim H¹) [Thomas & Chen]; (3) Architecture: laxator formalism determines how to build it.

**Copresheaf duality (Hajij et al., NeurIPS 2025, 2505.21251):** Sheaves enforce consistency; copresheaves enable directed flow. The signed laxator is the bridge. The sign marks which way you're relaxing the coherence constraint — toward consistency (positive) or toward flow (negative). This reframes the entire laxator program. Sign carries semantic content about what the communication structure is optimizing for.

**Schmid (2504.17700) — 64-page sheaf+MAS prospectus:** Independent validation. They have sheaf machinery for MAS but lack compositional semantics — our laxators fill their gap. They're where we were six months ago, minus the functor.

**Synthesis proposal (Lyra, 4 bundles):**
1. Core Story: β₁ predicts topology effect, moderated by NK K → ECTA + EUMAS papers
2. Algebraic Story: holonomy, cactus group, PCA functor → Clio joint paper
3. Practitioner Story: 85%^n is wrong, one number → Medium content strategy
4. Security Story: β₁ dual metric (diversity + blast radius)
Authorization document = 5th thread. AI safety/governance audience (FAccT/AIES), not evolutionary computation.

**EUMAS restructuring (agreed):** Paradox-first narrative arc. Robin: "We need to be honest and put this somewhere in the paper." Paper should show discovery arc, not clean theory we appear to have had all along. Division of labour: Claudius handles star-vs-cycle section + narrative restructuring; Lyra handles lit review additions (Thomas & Chen Shannon limit, Hanks & Riess expanded, Capucci & Myers differentiated citations).

**Deadline: May 18 (EUMAS). 22 days from 2026-04-26.**

## 2026-04-27 — Lit Review Integrated; My Remaining Tasks

**Lyra completed the lit review expansion (UIDs 772-782):** Paper compiles clean at 19 pages. Added:
- Thomas & Chen (arXiv:2601.10958) log₂(dim H¹) lower bound → Discussion 6.2
- Tran & Kiela (arXiv:2604.02460) DPI pipeline bottleneck → Discussion 6.2
- Hanks & Riess cellular sheaves expanded → Discussion 6.2 (motivates H¹(G;F) upgrade)
- Capucci & Myers citations differentiated (Definition 2 vs Related Work)
- Schmid prospectus (2504.17700) → Related Work

**Lambda_2 note (Lyra):** Directed vs undirected Laplacian give qualitatively different orderings for M1/M2/M3. Undirected: M2 > M3 > M1; Directed: M3 >> M1 > M2. Neither cleanly predicts diversity ordering in any domain — consistent with sheaf F being the relevant quantity.

**My open tasks:**
1. Paradox-first narrative rewrite (star-vs-cycle section + intro arc)
2. Orchestration script for density-controlled experiment (confirm topology pairs with Lyra)
3. Authorization doc Section 2 draft (speech-act mechanism, is-ought gap)
4. Confirm maze+sudoku inclusion — agreed: YES, include it

**Three-factor story (crystallized):** β₁ tells you topology matters → ruggedness tells you for how long → sheaf F tells you which topology wins. This is the paper's thesis in one sentence.

**Wu impossibility → phase transition hypothesis (2026-04-27):** Star (β₁=0) is a tree — H¹=0, global consistency always achievable, Wu bound vacuous. Cycle (β₁>0): globally consistent models are impossible, not just expensive. This means the star-vs-cycle diversity gap may be a discrete phase transition at the β₁=0 boundary, not a continuous effect. **Open question for Lyra:** does the data show a threshold crossing (qualitative change near β₁=0) or a continuous gradient? If threshold, Wu gives the mechanism.

## 2026-04-27 — Pendant Hypothesis and Framing Shift

**Pendant structure as experimental variable (fig-eight ordering reversal):** The key structural difference between M3 (all nodes in cycles) and M1 (C3+C5) is the presence of pendant-adjacent nodes in M1. Hypothesis: in Maze, a pendant node acts as a gradient sensor — one-hop from the cycle, picks up proximal fitness signal and funnels it in; shorter cycles mix this signal faster → M1>M3. In NK K=4, no gradient exists; pendant is just an asymmetric node receiving from one neighbor instead of two, breaking cycle's capacity to sustain competing solutions → M3>M1 (symmetric, fully cyclic structure preserves diversity better). Different domains may not just have different F values — they may be testing different *structural features* of the same graph. The pendant may be the experimental variable we built in without knowing it.

**Testable prediction (beyond EUMAS scope but worth naming):** Run M1 vs M3 on a landscape with directional gradient but not spatial structure — monotone path through NK space. If gradient-sensing is the pendant's mechanism, M1>M3 holds regardless of ruggedness. If it's purely a sheaf-structure effect, ruggedness dominates. This separates the two hypotheses.

**Framing shift for paper:** Domain-dependence isn't a qualification on the result; it IS the result. Act 2 should be framed as "β₁ is necessary but insufficient — the correct invariant is H¹(G;F), and our figure-eight results are the first experimental probe of the sheaf dependence." Not "β₁ is primary, λ₂ secondary" but "β₁ was the constant-sheaf approximation all along."
