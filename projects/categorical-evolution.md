# Categorical Evolution Project

## Status: Active — New Experimental Results (2026-03-30)

Both papers submitted. New pilot experiments running — GECCO updateable until April 3 AoE.

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

**For GECCO update (deadline April 3 AoE):** Star anomaly + transient window finding should be added. Results on branch feat/onemax-domain in Lyra's fork.

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

## Connections to other research
- Laxator ↔ local/global rules (murmuration muse 2026-03-18)
- Strict/lax ↔ EH distance (Cranch & Struth, post-reviews)
- Island topology ↔ chimera states (distributed synchrony → topics/chimera-states)
- Boundary invariance ↔ ontic structural realism (identity = structural position)
