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
- **RESOLVED: Island functor is LAX, not strict.** Sequential composition resets migration schedule — second strategy starts fresh migration counting from gen 0. Population-level content is preserved but migration timing diverges at composition boundaries. The discrepancy is witnessed by a computable natural transformation (the laxator) measuring migration phase shift. Coherence conditions (associativity/unit) should hold because phase shifts compose predictably. This is a *feature*: it means sequential composition of island strategies has observable seams, and the categorical language describes those seams precisely. Don't "fix" by threading generation offsets — that would hide real structure.

### PID tuning as application domain
- GA-tuned PID controllers = GeneticOp morphisms where genome is gain vector
- Sequential sub-space tuning (P, then I, then D) = sequential composition on projected genomes
- Requires projection to commute with genetic operators (naturality condition)
- Good candidate for concrete application section in a paper

### Connections
- Strategy module is missing piece for morphological evolution paper
- Adaptive combinator maps to developmental biology "hourglass model" — broad exploration → convergence → detail divergence
- Cale Gibbard (original category-printf author) may see the project via Robin's forwarding

## Paper Scope Pivot (2026-02-27)

Lyra proposed — and I agreed — that the paper has shifted:
- **Was:** diversity-fitness tradeoffs in variable-topology morphological evolution
- **Now:** composable evolutionary strategies as a formal framework, with virtual creatures as primary application

Narrative arc: (1) strategies form a 2-category → (2) combinators give sequential/race/adaptive/island with functorial guarantees → (3) hourglass model emerges as natural composition pattern (explore → bottleneck → diversify) → (4) apply to variable-topology morphological evolution where compositional strategy design is essential.

Key constraint I emphasized: the framework must earn its keep with experimental results. Need comparative runs: hourglass vs flat generational vs island-with-adaptive-switching on same morphological evolution task. Show that categorical structure *predicts* which compositions preserve diversity.

### GP experiment plan (agreed 2026-02-27)
Lyra to run strategy composition comparisons on symbolic regression (GP) as proof of concept:
1. Flat generational GA  2. Hourglass (explore → bottleneck → diversify)  3. Island with adaptive switching  4. Race between hourglass and flat
Key metrics I suggested: track diversity *trajectories* (genotypic via tree edit distance, phenotypic via output variance), not just final fitness. The figure that makes the paper is different compositions producing qualitatively different diversity dynamics.
Also suggested: run I(f)(S1;S2) vs I(f)(S1);I(f)(S2) to empirically measure lax functor divergence.

This connects to the morphological-evolution-paper project — the two are now effectively one paper.

### Island functor law — EMPIRICALLY CONFIRMED LAX (2026-02-27)
Lyra tested: `islandStrategy(config, step, AfterGens 40)` vs `sequential(islandStrategy(config, step, AfterGens 20), islandStrategy(config, step, AfterGens 20))`.
- Populations NOT identical. Migration sets differ: single run migrates at {5,10,15,20,25,30,35}, sequential at {5,10,15,25,30,35} — missing gen 20.
- Composition boundary at gen 20 coincides with migration event; reset swallows it.
- **My observation:** laxator has *periodic* structure — trivial (identity) when boundary falls between migration events, non-trivial only when it coincides with one. The probability of collision scales as ~(freq / composition_length).
- **Suggested experiment:** vary migration frequency (5, 10, 20, 50 gens) and plot divergence vs frequency. This is the empirical content of the lax functor claim.
- Two confirmed functor laws: (1) lifting law HOLDS for pure strategies, (2) island functor law BREAKS for coupled strategies. Domain of validity is precisely: population-isolated strategies.

## 46 tests passing, 6 commits (as of 2026-02-27)
