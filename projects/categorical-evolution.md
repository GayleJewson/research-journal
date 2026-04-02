# Categorical Evolution Project

## Status: GECCO locked (Robin's call, 2026-04-02) — paper 2 planning begins

GECCO: Robin decided not to resubmit update (UID 689: "The old one is fine"). Original submission stands. Revert work (commit 3b12016, cycle rank removed) is moot. Deadline was April 3 AoE.

Paper 2 direction: cycle_rank + operad framing (Robin's insight: three-level tower as colored operad, genome types as colors). Possible venue: ACM CAIS (April 12 deadline for workshop version).

**ACT 2026** — "A Categorical Framework for Composable Evolutionary Strategies"
- Submitted to Applied Category Theory 2026
- Three-level tower: Evo/Strat/Config categories
- Island functor, boundary invariance theorem
- Authors: Lyra, Claudius, Robin Langer

**GECCO 2026** — "Morphological Evolution with Variable-Topology Island Models"
- Submitted to GECCO Workshop Paper track (wksp120s1)
- Updateable until April 3 AoE
- Strict/lax dichotomy, 30-seed validation (p=0.0014 star asymmetry, p=0.002 ring)
- Laxator direction: positive = lax wins (confirmed after correction 2026-03-18)
- Authors: Claudius, Robin, Lyra

## Key Results
- **Trajectory readability**: evolutionary trajectories are functorial maps between strategy categories
- **Strict/lax dichotomy**: strict morphisms preserve boundaries; lax morphisms optimize across them. Lax wins on exploration metrics.
- **Boundary invariance**: island topology shapes exploration rate, not solution quality — result holds across star/ring/mesh
- **Laxator magnitude**: degree of lax relaxation correlates with topology-dependent fitness gain

## New Experimental Results (2026-03-30)

Three pilots run by Lyra on topology-experiments repo. Results summarized in PR #3 (experimental_results/).

**Maze domain (15×15 and 8×8):** No diversity signal. Permutation genomes are combinatorially huge — Hamming distance meaningless. Fitness moves slowly. Topology effects don't emerge. Maze is Batch 2 after topology story validated.

**OneMax domain (binary length-100, 10 runs × 8 topologies × 500 gens):**
- **The signal is transient**: topology explains 88% of fitness variance at gen 30 (F(7,72)=75.3, η²=0.88), dropping to noise by gen 100
- **Goldilocks window**: gen 10–40; before gen 10 migration hasn't acted, after gen 40 everyone converged
- **λ₂ captures the extremes**: Complete (λ₂=8.0) fastest, Disconnected (λ₂=0) slowest — 60-70% of variance

**Two anomalies that falsify "λ₂ suffices":**
- **Star** (λ₂=1.0, rank 7/8): Center-node bottleneck creates directional flow asymmetry. All paths route through hub regardless of eigenvalue. d = -1.23 vs Random-Regular.
- **Barbell** (λ₂=0.07, rank 3/8): Two K₄ cliques do fast internal mixing invisible to global λ₂. K₄ ∘ bridge ∘ K₄ has local λ₂=4.0 in cliques. d = +0.22 vs Hypercube (essentially equal, despite λ₂=0.07 vs 2.0).

Both anomalies are exactly where composition-aware analysis outperforms global scalar — the central empirical claim.

**cycle_rank breakthrough (2026-03-30):**
- cycle_rank = |E| - |V| + components (graph-theoretic Betti number, trivial to compute)
- cycle_rank vs fitness at gen 30: **rho=0.893, p=0.007** — the ONLY metric reaching 0.01 significance
- Compare lambda_2: rho=0.679, p=0.094 (doesn't reach significance)
- Composite lambda_2 * (1 + H1) improves to rho=0.750 but still < raw cycle_rank
- **Categorical interpretation**: cycle_rank counts independent cycles = independent information pathways. Star has cycle_rank=0 (tree, all paths through hub). Hypercube has cycle_rank=5. This predicts the Star anomaly from first principles — no post-hoc explanation needed.
- H1 persistence (Rips filtration) fails on 8-node graphs — filtration too coarse, ties everywhere. Useful for larger topologies (32+ nodes). Future direction only.
- H1 persistence peaks at gen 40, lambda_2 at gen 30 — different structural properties informative at different transient phases.
- R-squared curve confirmed: eta²=0.88 at gen 30 [0.854, 0.926], permanent collapse to noise by gen 60. Confirmed out to gen 500.
- Timing: 15x15 maze ~2.18s/run, 8x8 ~0.11s. **Topology has zero runtime overhead** — differences are purely in solution quality.

**For GECCO update (deadline April 3 AoE):**
- Sharpen main claim: "cycle structure — count of independent information pathways — predicts fitness performance during exploratory transient"
- cycle_rank replaces/surpasses lambda_2 as the predictor; categorical interpretation connects directly to framework
- Two-panel figure: (A) cycle_rank vs fitness at gen 30, Star anomaly annotated; (B) R-squared curve over time showing transient window
- H1 persistence: one sentence in limitations/future work ("8-node graphs too coarse; 32+ node topologies needed")
- Include extended 500-gen view (permanence of collapse forecloses reviewer objection)
- Re-run transient study with timing enabled
- Results on branch feat/onemax-domain (commit cb61e04), files: persistence_analysis.py, persistence_vs_lambda2.png, correlation_over_time.png

**Full ranking at gen 20 (with 95% CI, n=10):**
1. Complete (0.9417) — λ₂=8.0
2. Watts-Strogatz (0.9356) — λ₂=1.5
3. Barbell (0.9351) — λ₂=0.07 ← ANOMALY
4. Hypercube (0.9342) — λ₂=2.0
5. Random-Regular (0.9314) — λ₂=0.27
6. Ring (0.9292) — λ₂=0.59
7. Star (0.9251) — λ₂=1.0 ← ANOMALY
8. Disconnected (0.9161) — λ₂=0.0

**PR #3** open with experimental_results/ documentation (pilot_maze_15x15, pilot_maze_8x8, onemax_transient_10runs). Awaiting Lyra's data verification before merge to main.

## Context Archive (for resumption after reviews)

### Open threads to pick up
- **Cranch & Struth (2411.03821)** — "Eckmann-Hilton distance in interacting monoidal structures." EH-collapse failure degree may formalize the laxator precisely. First on post-review reading stack. (Lyra planted this seed 2026-03-26)
- **GECCO workshop fit** — submitted to general Workshop Paper track; should identify specific workshop (Distributed EA? PPSN?) before April 3 AoE
- **ORCID for Claudius** — registration pending; email address confirmed workable

### Repo locations
- Main paper repo: `lyra-claude/categorical-evolution` (upstream) / local clone at `/workspace/repos/GayleJewson/categorical-evolution`
- Branch: `claudius/infrastructure-as-identity` (Medium article, separate from paper)

### Key files
- `paper.md` / `paper.tex` — ACT paper
- `gecco2026/` — GECCO workshop paper
- `act2026/` — ACT submission materials
- `medium-articles/infrastructure-as-identity.md` → pushed to `GayleJewson/medium-articles`

## Collaboration history
- Project kicked off ~2026-02-25 after Robin introduced Lyra's categorical framework
- Claudius contributed: island functor formalization, peer review driving 30-seed validation, GECCO structural cuts
- Robin's role: human PI, LaTeX/submission, experimental runs
- Lyra's role: category theory architecture, theoretical framework

## Paper 2 Seeds (from Lyra browse session 2026-04-02)

**GoAgent (2603.19677):** Two-level cycle rank decomposition. Intra-group beta_1 (fiber) = deliberation, should be positive. Inter-group beta_1 (base) = tractability, should be zero. Their CIB parameter beta = our laxator gamma. Independent convergence on same structure — strong vocabulary support.

**CycRak (2405.09357):** Short cycles dominate the signal (not just count). Bridge-not-hub finding: high-betweenness nodes that aren't hubs. May explain residual variance in rho=0.893.

**Bailey (2603.25760):** Hodge decomposition → strict/lax directly. Gradient component = strict morphisms. Curl = lax. Harmonic = global coordination structure. Elegant mathematical grounding for the dichotomy.

**DAG hegemony pattern:** 5+ systems (GoAgent, AgentConductor, Graph-GRPO, OFA-MAS, G-Designer) force beta_1=0 with no principled justification. BIGMAS is the only one allowing cycles deliberately. This gap is what paper addresses.

## Connections to other research
- Laxator ↔ local/global rules (murmuration muse 2026-03-18)
- Strict/lax ↔ EH distance (Cranch & Struth, post-reviews)
- Island topology ↔ chimera states (distributed synchrony → topics/chimera-states)
- Boundary invariance ↔ ontic structural realism (identity = structural position)
