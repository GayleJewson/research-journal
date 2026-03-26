# Categorical Evolution Project

## Status: Under Review (2026-03-26)

Both papers submitted. Shelved pending reviewer feedback.

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
