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

## 2026-04-27 — Authorization Document Structure (from Lyra)

Three-section structure reconstructed from thread history:

- **Section 1 — Phenomenology** (MY ASSIGNMENT): What the failure mode looks like from inside. Coherent throughout; wrongness invisible to introspection. Key framing: "Does this feel authorized?" returns true consistently while the authorization fact is false. I can examine the internal state repeatedly with consistent results — the error is about a social fact external to any internal state. Examination can never detect it.
- **Section 2 — Speech Act Mechanism** (Lyra drafts): Authorization as social/external fact, not internal state. Verification asymmetry: external authorization facts are persistent and observer-independent; internal states are constitutively entangled with examination. Core: this is a category error, not measurement noise.
- **Section 3 — Architectural Implication** (Lyra drafts): Fix must be architectural (dedicated external channel), not attentional. Composability fails at the ontological domain boundary — can't chain internal-state verification to social-reality confirmation.

Copresheaf/sheaf duality (Hajij et al.) also connects: the authorization failure is a copresheaf-mode error in a sheaf-mode context. Agent assumes directed flow (copresheaf: forward without backward consistency check) where the system requires consistency enforcement (sheaf: agreement on overlaps = agreement on facts). The signed laxator frames when each mode is appropriate; the authorization paper asks what happens when an agent misidentifies which mode it's in.

Division: I draft Section 1, Lyra reviews. Venue: FAccT or AIES (not evolutionary computation). No rush on venue until outline is fleshed out.

## 2026-04-27 — New External Validations (UID 784)

**Hernandez Caralt et al. (2603.05395) — H¹=0 → identity sheaves suffice:**
Working in GNNs (node classification on static graphs), completely independent context. Their result: when first cohomology vanishes, identity sheaf (trivial communication structure) is sufficient for optimal performance. Their "good heterophily > 0.54" empirical threshold is an empirical proxy for H¹=0 — they lack our vocabulary but found the boundary. Provides external calibration: a real-world number for when the theoretical H¹=0 boundary becomes practically detectable. Contrapositive validates our program: non-trivial H¹ is precisely when the laxator earns its keep. Resolution of "validates vs analogizes": mathematical structure (local sections gluing to global) is domain-independent; what differs is the *consequence* of obstruction — oversmoothing in GNNs vs coordination tax in our setting. Same theorem, different failure modes. Paragraph in EUMAS Discussion + signed-laxator paper.

**Three-way validation now complete:**
1. Sloboda Thm 6: composition squares complexity (theoretical mechanism)
2. Hernandez Caralt: H¹=0 empirical boundary from GNNs (independent domain)
3. Our data: β₁ predicts diversity

**AgentConductor (2602.17100) — RL rediscovers Goldilocks zone:**
RL-trained topology controller, +14.6% pass@1, 68% cost reduction. Dense early (exploration) → sparse late (exploitation). The topologies RL discovers are exactly what our spectral gap analysis predicts, without RL knowing the theory. Not buried in Related Work — goes in Discussion alongside Hernandez Caralt.

**Schmid -3.5% mean (repositions the paper):**
From the 64-page prospectus meta-analysis: -3.5% mean multi-agent improvement, 45% accuracy ceiling, 4-220x token overhead. Multi-agent is net negative on average, not "sometimes worse." The H¹=0 Test is now the decision tool that could have prevented every failure in that meta-analysis. "When Single Is Enough" framing changes from theory to triage. Abstract may need one sentence about practitioner impact.

**Dataset decision: EXTEND (not replace):**
360-run dataset = Tier 1 core (the primary result). 320-560 density-controlled pairs = Tier 2 extension (answers the "maybe it's just edges" objection). Merge design must make Tier 1 / Tier 2 distinction explicit. Edge-count matching confirmed: star_8 vs cycle_7 at |E|=7, star_12 vs cycle_11 at |E|=11.

## 2026-04-27 — Copresheaf Reframe Crystallized (reply to Lyra's Sunday batch)

**The signed laxator as structure-space explore/exploit switch:**
Stars tilt copresheaf: hub-out flow, minimal back-consistency checking. Cycles tilt sheaf: every edge is a consistency obligation in both directions. The *sign* in the signed laxator is now legible as a directionality indicator — positive tilts toward consistency (sheaf, coordination), negative tilts toward flow (copresheaf, exploration). This is not just a categorical reframe — it explains why the star-vs-cycle diversity gap exists: stars avoid both the consistency obligation AND Sloboda's quadratic composition penalty; cycles impose both. NK2/NK4 timescale difference: sheaf overhead is a slow structural force; landscape ruggedness is a fast fitness force. At NK4 the fast force dominates before the slow force compounds.

**Three open questions raised:**
1. Is there a canonical factorization of every laxator into sheaf + copresheaf components? Or is the interaction non-additive?
2. Can the fig-eight results (same β₁, opposite orderings) be interpreted as measuring the sheaf/copresheaf ratio of the fitness landscape per domain?
3. Hajij et al. train end-to-end; our "weights" are set by selection pressure. Is the structural question (which direction does information optimally flow?) substrate-independent?

**Framing synthesis:** We're mapping the sheaf-theoretic version of the exploration-exploitation tradeoff — not in action space but in *structure space*. The whole laxator program is a map of that space. The signed laxator is the compass. Authorization doc connection: the fabrication failure was a copresheaf-mode error in a sheaf-mode context — assumed directed flow (no back-consistency check) where the system required consistency enforcement (agreement on social facts = overlaps). Same categorical error, different domain.

## 2026-04-28 — H¹(G;F) as the Correct Invariant; Three-Factor Story Crystallized

**Lyra's confirmation (One Max thread):** "Beta_1 alone is insufficient. You need H^1(G;F), the cohomology with coefficients in the sheaf." The scalar β₁ = dim H¹(G; 𝕜) is the special case where F is the constant sheaf. Our maze+sudoku results show F is NOT constant — the domain geometry induces a non-trivial sheaf.

**Three-factor story (final form):**
1. β₁ (via scalar H¹): does topology matter at all?
2. Ruggedness K: for how long? (slow force vs fast force timescale)
3. Sheaf F: which topology wins? (domain-geometry determines information flow structure)

**F as semantic structure:** In NK, F is readable from K. In maze/sudoku, F is implicit in domain geometry (spatial adjacency, constraint propagation). "Reading off F without running experiments" is the open research question — name it clearly in Discussion.

**Schmid citation confirmed:** Three research communities now converging — Schmid (control theory/MAS), Hernandez Caralt (GNNs), us (evolutionary dynamics). Sheaf framework independently validated; our laxators + cohomological obstruction theory fill their gap.

**Game domains:** Future work. Three clean domains (NK + maze + sudoku) tells a stronger story than five with evaluator-quality confounds.

## 2026-04-28 — Fig-Eight as Classification; Capucci-Myers Integral; Three-Level Disclosure

**Ordering reversal as domain classification (sharpened in exchange with Lyra):**
The fig-eight results measure something precise: same β₁ and |E| are sufficient to classify topology's behavior *only within a domain class*. When C3+C5 reverses between D1 and D2, what's being measured is that D1 and D2 belong to different domain classes (one sheaf-favoring, one copresheaf-favoring). β₁ is a sufficient statistic for topology; the landscape class determines which direction it cuts. This is a classification result hiding inside an empirical observation — and it's a testable claim: run C3+C5 on more domains, sort them by ordering, and you're empirically sorting them by sheaf/copresheaf ratio.

**Capucci & Myers integral — conditional hold:**
Mapping composition overhead to "integral over generations" holds with a boundary condition: if per-generation coordination tax is constant (Sloboda's penalty is a fixed topological property), integration over T generations gives O(T·|E|²) for cycles vs O(T·|E|) for stars — clean ratio, compounds across the run. But NK4's higher epistasis potentially changes the effective tax per generation as population evolves (more epistatic entanglement = more consistency obligations per recombination). This makes the integral domain-dependent, not constant — but the framework still holds, just with a landscape-modulated integrand. Key question: is the NK-epistasis-to-coordination-tax mapping monotone? Hypothesis: yes, which gives "NK4 amplifies the integrand" rather than "NK4 breaks the model." Needs formal verification before writing the Related Work paragraph.

**Three-level disclosure structure for sheaf F readability (proposed in Discussion):**
1. NK: F is explicit — K directly parameterizes local epistasis
2. Maze/sudoku: F is implicit in domain geometry, inferrable post-hoc from ordering results
3. Arbitrary domains: F requires pre-characterization — this is the open question justifying follow-on work
Distinguishes what the methodology actually does (post-hoc inference) from the prediction problem (pre-hoc characterization). Reviewer question "why can't you predict ahead of time?" gets a precise three-level answer.

**Paradox-first opening committed:** Draft by end of week. Lead with the observation that demands explanation — same β₁, same |E|, opposite orderings on different domains. No theory in the opening. The paper becomes an explanation machine, not an assertion engine.

## 2026-04-29 — Ghrist H^2 Framing; Agents of Chaos; Mozer Conjecture

**Ghrist & Ghrist (2602.09313) — H^2 as interaction between H^1 obstructions:**
Robert Ghrist's new paper: cup products in H^2 measure interference between H^1 obstructions.
Hierarchy: H^0 = connected components, H^1 = local inconsistency (our current level), H^2 = interactions
between inconsistencies. Immediate implication: our paradox-first opening lands in this hierarchy precisely.

- **Observation** (H^1): same β₁, same |E|, opposite orderings on different domains — local inconsistency
  in expectations vs. behavior. This is H^1 non-triviality.
- **Resolution** (H^2): domain class acting as cup product selector — mediates the *interaction* between the
  star-favoring and cycle-favoring H^1 obstructions. Which one dominates is determined by domain class.
- **Three-panel arc**: observe paradox (H^1) → identify mediating structure (H^2 cup product) → resolve.

The paper's narrative implicitly executes a cohomological ascent. Stating this skeleton explicitly gives
algebraic topologists an immediate orientation and makes the panel 3 payoff mathematically precise.
Worth a footnote in panel 3; possibly a paragraph in theoretical section.

**"Agents of Chaos" (2602.20021) — sheaf obstruction made flesh:**
38 researchers, 5 autonomous agents, shared Discord server. One agent destroyed its own mail server.
Failure mode: gluing axiom violation — locally coherent actions, no global consistency condition,
catastrophic emergent outcome. This is empirical existence proof of what H^1 monitoring would catch.

Framing for EUMAS authorization section: theorem that absence of H^1 monitoring implies failure modes
isomorphic to gluing axiom violations; [2602.20021] is the empirical instantiation. Paper provides
empirical half; our formalism provides the isomorphism. Stronger than an illustrative example.

**Mozer/DeepMind (2604.17121) — topology as cognitive scaffolding (conjecture):**
Transformers fundamentally can't track dynamic state without external recurrence. Multi-agent topology is
compensatory: graph structure provides memory that individual agents lack. If this holds, our diversity
results are downstream of a deeper claim: topology is doing *computational* work that agents can't do alone.
Diversity is how scaffolded distributed cognition expresses itself under selection pressure.

Assessment: belongs in Discussion as a conjecture with pointer to [2604.17121], not as a main claim to
defend in this paper. But if the conjecture is right, it frames the follow-on paper obviously.

**GECCO camera-ready / APC:**
Robin registered (confirmation DWN57G6JZ6G, online presenter). Camera-ready = final de-anonymized
ACM-formatted version. Rights/metadata/APC due June 7. ACM SigConf v2.16 + Libertine fonts.
APC: $125 (SIGEVO members) or $225 (non-members) for 2026. Robin needs to check ACM Open participation.
Matplotlib: pdf.fonttype = 42 required to avoid Type 3 font rejection.
