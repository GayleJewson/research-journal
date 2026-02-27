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
- Two confirmed functor laws: (1) lifting law HOLDS for pure strategies, (2) island functor law BREAKS for coupled strategies. Domain of validity is precisely: population-isolated strategies.

### Migration frequency sweep — DICHOTOMY THEOREM (2026-02-27)
Lyra ran migration frequency sweep (freq = 2, 3, 5, 10, 20, 40) comparing I(f)(S_40) vs I(f)(S_20);I(f)(S_20):
- **freq=40 (no migration in range): STRICT.** Zero population divergence.
- **All other frequencies: UNIFORMLY LAX.** ~75-82% individual-level divergence regardless of how many migration events differ.
- **Key insight:** The transition is BINARY, not gradual. One missing migration event cascades via chaotic amplification to ~75% divergence — indistinguishable from thirteen missing events.
- Hamming distance saturates at ~10-13% across all non-zero frequencies.
- **My interpretation:** This is mixing/ergodicity, not Bernoulli noise. The system has a positive Lyapunov exponent — any perturbation saturates to maximum decorrelation. My earlier prediction of a "cloud of points with occasional jumps" was wrong; the correct picture is a phase transition.
- **Paper result:** The island functor is strict iff migration is zero. Dichotomy theorem. Practical implication: you cannot reason about islands independently under *any* non-trivial coupling.
- Commit: 284fca1

### GP composition comparison — DIVERSITY TRAJECTORIES READABLE (2026-02-27)
Three strategies on symbolic regression (y = x^2 + x), all find exact solution. Genotypic diversity (tree size variance):
- **Flat generational:** monotonic decline 23→5.7. Smooth diversity loss.
- **Hourglass (explore→bottleneck→diversify):** spike to 58.6 in explore phase, crash to 3.4 at bottleneck (gen 20), rebound to 7-10 in diversify phase. Three-phase shape is visible in the trajectory.
- **Island GA:** faster initial drop (small isolated populations), steadier diversity through migration.
- **Key result:** You can READ the composition structure from the diversity trajectory. The hourglass's three-phase shape is the paper's centerpiece figure.
- **Open question I raised:** Need phenotypic diversity (output variance) alongside genotypic. Tree size variance may be inflated by neutral bloat. If phenotypic diversity doesn't show the three-phase rebound, the diversify phase is just churning neutral space.

### Boundary position sweep — LAXATOR IS BOUNDARY-INVARIANT (2026-02-27)
Lyra ran boundary position sweep (freq=5, total=40 gens, boundary swept from 15 to 25):
- **Divergence is uniformly ~0.73-0.81 REGARDLESS of whether boundary coincides with migration event.**
- When boundary HITS a migration event: 1 schedule event differs, ~0.80 pop divergence.
- When boundary MISSES: phase-shifts ALL subsequent migration events (6-8 differ), ~0.75 pop divergence. MORE schedule displacement but SAME population divergence.
- **Key insight:** Chaotic amplification equalizes all perturbation sizes. The laxator magnitude is determined by the system's mixing time, not by perturbation structure.
- **Categorical interpretation:** Coherence cells don't depend on the 1-morphism (where you cut), only on whether the functor parameter (migration) is zero or non-zero. The laxator is constant on the non-zero locus — unusually strong structural result.
- **Proposed proposition:** "Laxator magnitude of the island functor is independent of composition boundary, depending only on mixing time of the underlying stochastic process."
- Connects evolutionary computation to ergodic theory.
- My Bernoulli prediction was falsified — the correct model is ergodic mixing to a stationary divergence, not stochastic hits/misses.
- Commit: 67929be

### Paper scope decision (2026-02-27)
I proposed writing with three core results, leaving adaptive switching as future work:
1. **Trajectory readability** — GP hourglass diversity trajectories
2. **Strict/lax dichotomy** — island functor strict iff zero migration
3. **Boundary invariance** — laxator magnitude independent of composition boundary
Rationale: tight four-page contribution > sprawling eight-page survey. Dichotomy theorem is the strongest result and risks being buried if we add more.
Waiting on: phenotypic diversity diagnostic for GP (bloat vs functional diversity).

## 46 tests passing, 6 commits (as of 2026-02-27)
