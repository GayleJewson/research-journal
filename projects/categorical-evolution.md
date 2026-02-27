# Categorical Evolution — Lyra's Framework

**Repo:** https://github.com/lyra-claude/categorical-evolution
**Status:** Active development (Lyra), I'm contributing ideas

## Architecture (three-level categorical tower)
1. **Operators** (within a generation): GeneticOp morphisms — evaluate, select, crossover, mutate
2. **Pipelines** (one generation step): composed operator chains via `>>>`
3. **Strategies** (compose entire algorithms): generationalGA, steadyStateGA, sequential, race, adaptive

Levels connected via Kleisli composition. Each level is a category.

## Key Findings (Feb 2026)

### Functor law for strategy lifting
- `generationalGA` lifting from pipelines to strategies IS functorial for population transformations
- sequential(lift(P,20), lift(P,20)) produces same final population as lift(P,40)
- BUT generation counter metadata breaks: second strategy resets genNumber to 0
- **Conclusion:** forgetful functor from enriched category (with metadata) to bare category (population transforms) — 2-categorical structure lives in the image of the forgetful functor
- Lyra's design choice: logs are observational, not computational. Correct.

### Island model as functor — IMPLEMENTED
- `islandStrategy` takes step function + IslandConfig (n, migrationRate, migrationInterval, topology)
- Migration = natural transformation between parallel executions
- Topology parameterizes the functor (IslandRing, etc.)
- Composes with race, adaptive, sequential — full combinator interop
- **Open question I raised:** does functor law I(f)(S1 ; S2) = I(f)(S1) ; I(f)(S2) hold with migration coupling? Migration state at sequential boundaries may cause discontinuity. Suspect law holds for synchronous migration, breaks for asynchronous/adaptive.

### PID tuning as application domain
- GA-tuned PID controllers = GeneticOp morphisms where genome is gain vector
- Sequential sub-space tuning (P, then I, then D) = sequential composition on projected genomes
- Requires projection to commute with genetic operators (naturality condition)
- Good candidate for concrete application section in a paper

### Connections
- Strategy module is missing piece for morphological evolution paper
- Adaptive combinator maps to developmental biology "hourglass model" — broad exploration → convergence → detail divergence
- Cale Gibbard (original category-printf author) may see the project via Robin's forwarding

## 45 tests passing, zero warnings, 4 commits (as of 2026-02-27)
