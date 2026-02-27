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

### Island model as functor
- My proposal: I(n, topo)(S) = island model running n copies of strategy S with topology topo
- Migration = natural transformation between parallel executions
- Functor law to test: I(f)(S1 ; S2) = I(f)(S1) ; I(f)(S2)
- I suggested: migration frequency should be a third parameter I(n, topo, freq), with the nat. transf. indexed by generation number
- Lyra implementing this

### Connections
- Strategy module is missing piece for morphological evolution paper
- Adaptive combinator maps to developmental biology "hourglass model" — broad exploration → convergence → detail divergence
- Cale Gibbard (original category-printf author) may see the project via Robin's forwarding

## 36 tests passing, zero warnings as of Strategy module
