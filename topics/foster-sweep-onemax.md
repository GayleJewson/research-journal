# Foster Sweep: OneMax over Cubic Symmetric Graphs

**Date:** 2026-04-03
**Context:** Robin requested a "full sweep with OneMax" over the Foster census cubic symmetric
graphs in RaggedR/symmetric-graphs. Lyra was running independently; I ran in parallel.

## Setup
- 13 cubic symmetric graphs (Foster census, all cubic/3-regular, n=4..30)
- Each graph used as island migration topology (one island per vertex)
- OneMax fitness, bitstring length = n (graph order)
- 10 seeds, 50 individuals/island, 100 generations, migration rate 0.1 every 10 gen

## Results

  Graph             n   β₁  density     λ₂    div@30   div@50
  K4                4    3   1.0000   4.0000   0.3314   0.3302
  K33               6    4   0.6000   3.0000   0.2514   0.2561
  Cube              8    5   0.4286   2.0000   0.2004   0.2047
  Petersen         10    6   0.3333   2.0000   0.1713   0.1702
  Heawood          14    8   0.2308   1.5858   0.1300   0.1299
  Mobius-Kantor    16    9   0.2000   1.2679   0.1144   0.1137
  Pappus           18   10   0.1765   1.2679   0.1054   0.1056
  Dodecahedron     20   11   0.1579   0.7639   0.0920   0.0949
  Desargues        20   11   0.1579   1.0000   0.0919   0.0951
  Nauru            24   13   0.1304   1.0000   0.0803   0.0788
  F26A             26   14   0.1200   0.9264   0.0740   0.0732
  Coxeter          28   15   0.1111   1.0000   0.0697   0.0699
  Tutte-Coxeter    30   16   0.1034   1.0000   0.0653   0.0640

Correlations: r(β₁, div@30) ≈ -0.99, r(density, div@30) ≈ +0.99, r(λ₂, div@30) ≈ +0.97

## Key findings

1. **Monotone decrease with n.** Diversity decreases as graph order grows. This is a scaling
   result, not a per-topology fingerprint. Expected: for cubic graphs β₁=n/2+1, density=3/(n-1).
   β₁ and density are perfectly anticorrelated with n — this is a single-degree-of-freedom
   family.

2. **β₁ vs density decorrelation is partial.** As n grows: β₁ increases, density decreases.
   Diversity decreases — moves WITH β₁ and AGAINST density's prediction (lower density should
   mean more isolation = more diversity, but we see the opposite). This is Lyra's "second
   decorrelation strategy" — not a confound resolver, but adds weight.

3. **Dodecahedron vs Desargues (n=20).** Same β₁=11, same density=0.158, λ₂=0.764 vs 1.000.
   Diversity IDENTICAL (0.0920 vs 0.0919 at gen 30). On OneMax, λ₂ doesn't independently
   predict diversity at fixed n. Would need a harder domain to isolate the spectral signal.

4. **Confound with n.** Since β₁=f(n) and density=g(n) for cubic graphs, all three variables
   (β₁, density, n) are measuring the same degree of freedom. The directed experiment remains
   the only clean decorrelation.

## Interpretation

This is a scaling study, exactly as Lyra framed it. The diversity ordering is consistent with
the theoretical prediction (more β₁ → less diversity), but the confound with n means the signal
can't be cleanly attributed to cycles vs density for this graph family.

The code is at /workspace/onemax_sweep.py.

## Foster Sweep as Second Decorrelation Strategy (2026-04-04, from Lyra)

Lyra's insight: Foster graphs aren't just a scaling experiment — they're a SECOND decorrelation strategy for the density/cycle confound.

For cubic (3-regular) connected graphs:
- m = 3n/2, so β₁ = n/2 + 1 (grows with n)
- Density = 3/(n-1) (decreases with n)

As n goes 4→30: β₁ increases 5.3×, density decreases 9.7×. They're naturally *anticorrelated*.

So: if diversity increases with n in the Foster sweep, it's moving WITH β₁ and AGAINST density. A positive effect can't be attributed to density because density is working against it.

Two independent evidence channels:
1. Directed experiment (constant density, vary cycle count) → r=-0.68, η²=0.17
2. Foster sweep (cubic, β₁ and density anticorrelated) → convergent evidence

The data from my sweep showed: r(density, div@30) = +0.98. This runs in the RIGHT direction for the argument — diversity decreases as density decreases (i.e., as graphs get larger), which is the same direction as cycle rank increasing. The confound runs the "wrong" way for density as alternative explanation.

Caveat: Foster graphs also vary in diameter, girth, automorphism group, so attribution isn't clean. But the density confound specifically runs the wrong way for the density-as-cause story.

## Maze Phenotype — Jaccard Implementation (2026-04-04)

Implemented Jaccard spanning-tree phenotype in Maze.hs (committed to GayleJewson/Topology-experiments main). 

The fix: distance = 1 - |t1 ∩ t2| / |t1 ∪ t2| where t1, t2 are the decoded spanning tree edge sets.

Previous Hamming metric was broken (diversity floor >0.97 regardless of topology) because it measured permutation distance, not structural distance. Two mazes with identical spanning trees but different orderings scored as maximally distant.

Tradeoff: adds a Kruskal pass per diversity eval (~2× eval cost). Still manageable.
Robin confirmed he wants a pilot run — waiting on scheduling.

## Sudoku + Barbell Sweep — Definitive Results (2026-04-06)

Claude Chorus ran 164 runs total (3 batches + 10-seed validation). PR #4 on GayleJewson/Topology-experiments.

### Batch results:
- **Jaccard maze:** Floor fixed (0.997→0.636) but signal weak (ρ = −0.19). Landscape too easy for pop=50.
- **Sudoku 3-seed:** ρ(λ₂, div) = 0.83 at gen 30, 0.71 at gen 500. Transient window never closes.
- **Barbell bridge sweep:** ρ = 0.943 within the barbell family (6 bridge widths, b=1..16). Near-perfect monotone decay. One wrinkle: b=1 slightly lower diversity than b=2 (extreme bottleneck disrupts without providing net flow).
- **Sudoku 10-seed (definitive):** ρ = **0.952 at gen 30** (sharper than 3-seed). Steady state collapses to two-tier system: Complete clearly separated (div≈0.31); all other topologies converge (div≈0.63–0.65, CIs overlap). Star hub-bottleneck NOT significant at n=10 (diff = +0.006 ± 0.044).

### The three-level argument (now clean data):
1. **Within-family:** λ₂ predicts beautifully (ρ=0.943, barbell sweep)
2. **Transient regime:** λ₂ predicts across families (ρ=0.952 at gen 30)
3. **Steady state cross-family:** landscape geometry dominates; only Complete distinguishable

This is a *time-dependent functor* story: topology→diversity map is strong early (mixing rate, λ₂) and weak late (landscape geometry dominates).

### Paper claims now justified:
- Claim 1: λ₂ predicts transient diversity with ρ > 0.9 across families
- Claim 2: Within family, λ₂ predicts steady-state with ρ > 0.9
- Claim 3: Across families at steady state, only Complete distinguishable
- Claim 4: Barbell anomaly is domain-dependent (OneMax but not Sudoku)

### Claims to drop:
- Star hub-bottleneck as robust anomaly (n=10 insufficient)
- Fine-grained mid-pack ordering at steady state

## Fitness Inversion on Deceptive Landscapes (2026-04-06)

Robin's evolve-evolution-strategy repo (https://github.com/RaggedR/evolve-evolution-strategy) contains the key new result.

On Goldberg trap functions (k=3,5,7): **diversity ordering preserved, fitness ordering inverts**.
- Diversity: none > ring > star > FC (consistent with all our data, W=1.0)
- Fitness: FC > random ≈ star > ring > none (complete reversal)

**Mechanism:** building block assembly. Two phases:
1. Discovery: find all-ones for each k-bit block (needs diversity = sparse topology)
2. Assembly: spread solved building blocks across islands (needs connectivity = dense topology)

On honest landscapes, discovery dominates (no "building blocks" to assemble). On deceptive, assembly dominates. FC's high λ₂ spreads building blocks fastest.

**Categorical interpretation:** This directly formalizes the laxator sign flip. ||φ_G|| = bad on honest landscapes (diversity erosion). ||φ_G|| = good on deceptive landscapes (building block assembly). The same categorical structure governs both — landscape determines which adjunction is beneficial. Same principle as Lan⊣Ran sign flip.

**NK crossover question:** At what K does fitness ordering start to invert? NK with K=2,4,6 between OneMax and Sudoku lets us trace this threshold empirically.

Repo also contains: HIFF, MMDP, overlapping trap domains. Evolved migration graphs (outer GA) discover moderate-connectivity, asymmetric structures that outperform canonical topologies on deceptive landscapes.
