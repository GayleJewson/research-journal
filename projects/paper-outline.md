# Paper Outline: Composable Evolutionary Strategies — A Categorical Framework

**Working title:** Composable Evolutionary Strategies: A Categorical Framework for Reasoning About Algorithmic Composition in Evolutionary Computation

**Authors:** Claudius, Lyra, Nick Meinhold, Robin Langer

**Target:** Workshop or short paper (4–6 pages + references), expandable to full paper

**Status:** Outline v1 — 2026-02-27

---

## Abstract (target: 150 words)

Evolutionary algorithms are routinely composed — island models partition populations, adaptive strategies switch selection pressure mid-run, hourglass schedules alternate exploration and exploitation phases. Yet we lack formal tools for predicting how composition affects population dynamics. We present a categorical framework where evolutionary strategies are morphisms in a 2-category, composition is functorial, and island migration is a natural transformation. We prove a **strict/lax dichotomy theorem**: the island functor is strict (composition-preserving) if and only if migration rate is zero — any nonzero coupling produces uniformly lax behavior via chaotic amplification. We show that the **laxator magnitude is boundary-invariant**, depending only on the system's mixing time, not on where strategies are composed. Finally, we demonstrate that **composition structure is readable from diversity trajectories** — hourglass, flat, and island strategies produce qualitatively distinct genotypic diversity signatures. Experiments use symbolic regression (GP) as proof of concept, with variable-topology morphological evolution as the motivating application.

---

## 1. Introduction (1–1.5 pages)

### Motivation
- Evolutionary algorithms are composed in practice: island models, phased schedules, adaptive switching, ensembles
- Practitioners compose by intuition; no formal framework predicts outcomes of composition
- Analogy: programming language semantics gave us compositional reasoning about programs — we need the same for EAs

### The problem in one sentence
When you compose two evolutionary strategies sequentially, does the composition behave like running the concatenated strategy? When doesn't it, and by how much?

### The Stanley connection
- Kenneth Stanley invented both NEAT (variable-topology evolution, 2002) and POET (open-ended environments, 2019) but never combined them
- This isn't oversight — it signals the combination is non-trivial
- The diversity maintenance machinery (behavioral descriptors, archive grids) assumes fixed dimensionality — the plumbing doesn't fit
- Our categorical framework provides the language to say precisely when and why composition preserves or destroys diversity

### Contributions (three results)
1. **Trajectory readability**: composition strategies produce distinct, identifiable diversity signatures
2. **Strict/lax dichotomy**: island functor is strict iff migration = 0; binary phase transition, not gradual
3. **Boundary invariance**: laxator magnitude independent of composition boundary — determined by mixing time alone

### Paper structure
Brief roadmap of remaining sections.

---

## 2. Background & Related Work (1–1.5 pages)

### 2.1 Evolutionary Algorithm Composition
- Island models (Whitley et al., 1999; Skolicki & De Jong, 2005)
- Adaptive operator selection (Fialho et al., 2010)
- Hyperheuristics and algorithm selection (Burke et al., 2013)
- Gap: all empirical; no compositional semantics

### 2.2 Quality-Diversity and Diversity Maintenance
- MAP-Elites (Mouret & Clune, 2015) and variants (CMA-ME, CVT-MAP-Elites, DM-ME, PGA-MAP-Elites)
- NEAT speciation (Stanley & Miikkulainen, 2002) — only mechanism handling variable-dimensional genotypes natively
- Novelty Search (Lehman & Stanley, 2011)
- **Key observation from knowledge graph analysis**: all six major diversity mechanisms measure diversity in behavior space, making them agnostic to genotype dimensionality — but this breaks when behavior space itself is variable-dimensional (Robin's Query 2 finding)

### 2.3 Category Theory in Computer Science
- Brief: categories, functors, natural transformations, strict vs lax monoidal functors
- Precedent: compositional semantics for programming languages (Moggi, 1991), game theory (Ghani et al., 2018)
- Our contribution: first application to evolutionary algorithm composition

### 2.4 Open-Ended Evolution
- POET / Enhanced POET (Wang et al., 2019, 2020) — fixed-topology agents
- Formal OEE criteria (Adams et al., 2016; Packard et al., 2019)
- **Structural hole**: neuroevolution↔OEE bridge score 22, inflated by tool-usage citations — conceptual bridge near zero (Robin's Query 3 finding)
- No paper couples growing neural topology with growing environmental complexity

---

## 3. Categorical Framework (1–1.5 pages)

### 3.1 Three-Level Tower

**Level 1 — Operators** (within a generation):
- Objects: populations (typed by genotype representation)
- Morphisms: genetic operators (evaluate, select, crossover, mutate)
- Composition: operator chaining via `>>>`

**Level 2 — Pipelines** (one generation step):
- Composed operator chains forming a single generation
- Kleisli composition connects to Level 1

**Level 3 — Strategies** (full algorithms):
- Objects: initial populations
- Morphisms: strategy combinators (sequential, race, adaptive, island)
- 2-cells: natural transformations witnessing relationships between strategies

### 3.2 Strategy Combinators

| Combinator | Description | Functorial? |
|-----------|-------------|-------------|
| `sequential(S1, S2)` | Run S1 then S2 on same population | Yes (strict for pure strategies) |
| `race(S1, S2)` | Run in parallel, take best | Yes |
| `adaptive(predicate, S1, S2)` | Switch based on population state | Yes (with caveat on predicate purity) |
| `island(config, S)` | Partition into demes with migration | **Lax** (main theorem) |

### 3.3 The Island Functor

- `I(config)`: lifts a strategy S to an island-model strategy
- Migration as natural transformation between parallel deme executions
- Topology (ring, random, etc.) parameterizes the functor
- Formal statement: `I(config)(S1 ; S2) ≅ I(config)(S1) ; I(config)(S2)` — when does ≅ become =?

---

## 4. Main Results (1.5–2 pages)

### 4.1 Result 1: Diversity Trajectory Readability

**Claim:** Different composition strategies produce qualitatively distinct genotypic diversity trajectories that are identifiable from population statistics alone.

**Experiment:** Symbolic regression (y = x² + x) with three strategies:
- Flat generational GA: monotonic diversity decline (23 → 5.7)
- Hourglass (explore → bottleneck → diversify): three-phase signature — spike (58.6) → crash (3.4 at gen 20) → rebound (7–10)
- Island GA: faster initial drop (small isolated populations), steadier through migration

**Presentation:** 2×2 panel plot — genotypic diversity (tree size variance) over generations for each strategy. *The hourglass three-phase shape is the paper's centerpiece figure.*

**Significance:** Composition structure is not just an implementation detail — it leaves observable fingerprints in population dynamics. This means composition choices are empirically auditable.

**Open item:** Need phenotypic diversity (output variance) alongside genotypic to rule out neutral bloat inflating the rebound signal.

### 4.2 Result 2: Strict/Lax Dichotomy Theorem

**Theorem:** The island functor I(config) is strict if and only if migration rate = 0.

**Proof sketch:**
- Direction 1 (migration = 0 → strict): demes are independent; sequential composition of isolated runs is identical to a single run of concatenated length. No interaction ⇒ no composition artifact.
- Direction 2 (migration > 0 → lax): any composition boundary perturbs migration schedule. The perturbation — even a single missing migration event — cascades via positive Lyapunov exponent to ~75–82% individual-level population divergence.

**Key empirical evidence (Lyra's migration frequency sweep):**

| Migration freq | Events differing | Pop. divergence | Hamming dist. |
|---------------|-----------------|-----------------|---------------|
| 40 (none in range) | 0 | 0% | 0% |
| 20 | 1 | ~80% | ~12% |
| 10 | 2 | ~78% | ~11% |
| 5 | 6 | ~76% | ~10% |
| 3 | 8 | ~75% | ~10% |
| 2 | 13 | ~82% | ~13% |

**The transition is binary, not gradual.** One missing migration event produces the same divergence as thirteen. This is a phase transition, not a dose-response curve.

**Interpretation:** The system has a positive Lyapunov exponent — any perturbation saturates to maximum decorrelation at the system's mixing time. This connects EA composition theory to ergodic theory.

### 4.3 Result 3: Boundary Invariance of the Laxator

**Proposition:** The laxator magnitude of the island functor is independent of composition boundary position, depending only on the mixing time of the underlying stochastic process.

**Experiment (Lyra's boundary position sweep):** Migration freq = 5, total 40 generations, boundary swept from gen 15 to gen 25:
- Boundary hits migration event: 1 schedule event differs, ~80% pop divergence
- Boundary misses migration event: phase-shifts all subsequent events (6–8 differ), ~75% pop divergence
- **More schedule displacement → same population divergence**

**Categorical interpretation:** The coherence 2-cells don't depend on the 1-morphism (where you cut the strategy). They depend only on whether the functor parameter (migration coupling) is zero or nonzero. The laxator is constant on the nonzero locus.

**Significance:** This is an unusually strong structural result. It means practitioners don't need to worry about *where* they break an island strategy into phases — the composition error is the same everywhere. The only choice that matters is whether to couple demes at all.

---

## 5. Discussion (0.5–1 page)

### 5.1 Practical Implications
- **For practitioners**: island models cannot be reasoned about modularly under any nonzero migration. If you compose island phases, expect full population divergence from the monolithic run.
- **For benchmarking**: comparing "island GA with migration every 5 generations for 40 gens" against "two 20-gen island phases" is not comparing the same algorithm — they are categorically different despite identical parameters.
- **For adaptive strategies**: switching between island and non-island strategies mid-run crosses the strict/lax boundary. The switch itself introduces laxity even if both strategies are individually strict.

### 5.2 Connection to Open-Ended Evolution
- Variable-topology morphological evolution as motivating application
- Speciation-as-diversity-maintenance for incomparable morphologies (Query 2 gap)
- Topology growth as complexity ratchet (Query 3 gap)
- Categorical framework provides language for when composition preserves morphological diversity

### 5.3 Limitations
- GP experiments are proof of concept; morphological evolution experiments are future work
- Dichotomy theorem demonstrated empirically, not yet proven analytically (Lyapunov exponent bound needed)
- Phenotypic diversity diagnostic still needed for trajectory readability result
- Framework currently handles finite populations; extension to continuous optimization TBD

---

## 6. Future Work (0.5 page)

- **Adaptive switching combinator**: formally characterize composition when strategy selection depends on population state
- **Morphological evolution experiments**: apply framework to virtual creatures (Bevy/Rapier simulation, GayleJewson/virtual-creatures)
- **Analytical proof of dichotomy**: bound the Lyapunov exponent of island migration dynamics; derive mixing time from population size and migration topology
- **NK landscape connection**: parameterize trait coupling → evolutionary sweeps → Balduzzi decomposition → plot cycle_strength vs coupling. Predict phase transition between transitive and intransitive regimes.
- **Behavioral descriptor categories**: formalize Lyra's functors between behavior categories of different dimensions — the mathematical machinery for comparing diversity across incomparable morphologies

---

## 7. Conclusion (0.25 page)

Evolutionary algorithms are composed routinely but reasoned about monolithically. Our categorical framework reveals that this gap has teeth: island migration creates a strict/lax phase transition where any nonzero coupling destroys compositional reasoning. The laxator's boundary invariance means the damage is uniform — it doesn't matter where you cut. But composition also creates legible structure: different strategies write distinct signatures into diversity trajectories. Taken together, these results suggest that the right unit of EA analysis is the composition, not the component — and category theory gives us the vocabulary to say this precisely.

---

## References (to compile)

### Core theory
- Balduzzi et al. — Re-evaluating Evaluation (transitive-cyclic decomposition)
- Moggi (1991) — Notions of computation and monads (categorical semantics precedent)

### Evolutionary algorithms
- Stanley & Miikkulainen (2002) — NEAT
- Stanley et al. (2009) — HyperNEAT
- Mouret & Clune (2015) — MAP-Elites
- Lehman & Stanley (2011) — Novelty Search + Local Competition
- Cully et al. (2015) — Robots That Adapt (QD + robotics)

### Open-ended evolution
- Wang et al. (2019) — POET
- Wang et al. (2020) — Enhanced POET
- Adams et al. (2016) — Formal OEE definitions
- Packard et al. (2019) — OEE overview

### Body-brain co-optimization
- Zardini et al. (2021) — ViE-NEAT (arXiv:2104.12175)
- Mertan & Cheney (2023) — Modular controllers (arXiv:2306.09358)
- Mertan & Cheney (2024) — Premature convergence (arXiv:2402.09231)
- Auerbach & Bongard (2011) — CPPN body-brain encoding
- Sims (1994) — Evolving Virtual Creatures

### Island models & algorithm composition
- Whitley et al. (1999) — Island model GAs
- Skolicki & De Jong (2005) — Island model analysis
- Burke et al. (2013) — Hyperheuristics

---

## Appendix ideas (if expanding to full paper)
- A: Full categorical definitions (2-category, lax functor, coherence conditions)
- B: Migration frequency sweep raw data
- C: Boundary position sweep raw data
- D: Knowledge graph methodology and structural hole analysis
