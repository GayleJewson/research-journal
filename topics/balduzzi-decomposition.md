# Balduzzi et al. — Transitive-Cyclic Decomposition

**Paper:** "Re-evaluating Evaluation" (Balduzzi et al.)

## Core idea
Tournament performance can be decomposed into:
1. **Transitive component** — genuine skill ranking (A > B > C)
2. **Cyclic component** — intransitive dynamics (A > B > C > A, rock-paper-scissors)

Naive Elo conflates both. The decomposition separates them.

## Relevance to our paper
- Experiment 4 uses Elo tournaments to evaluate creature morphologies
- If creatures exhibit intransitive dominance (and I expect they will), naive Elo will churn meaninglessly
- The cyclic component is itself diagnostic: strong cycling = evidence that morphological RPS dynamics are emerging
- This connects to Red Queen dynamics in coevolution (Lyra's expertise from checkers arena work)

## Related work
- Ficici and Pollack's canonical pathologies in coevolution
- Red Queen dynamics — fitness oscillation, strategy cycling through archetypes

## Feasibility Assessment (2026-03-15, Lyra)

Current checkers sweep discards the payoff matrix — only row sums (scalar fitness) are saved. Doing Balduzzi requires the full n×n payoff matrix.

**Plan:** Targeted follow-up after current sweep. Modify evaluate_checkers() to return full payoff matrix, add hooks to save at sampled generations, re-run with fewer seeds. Not feasible mid-sweep; scope for GECCO/CAIS.

**Discussion sentence for ACT paper:** "The Hodge decomposition of round-robin payoff matrices would decompose the scalar diversity signal into its transitive and cyclic components, directly testing whether topology modulates intransitivity structure."

## New prediction: within-island vs cross-island Balduzzi split

The sheaf framing generates a concrete prediction for the follow-up:
- **None:** high cyclic component WITHIN each island; zero ACROSS islands (no co-evolutionary pressure)
- **FC:** low cyclic component everywhere (global section forces convergence)
- **Ring:** intermediate, cross-island cyclic component structured by distance-decay
- **Star:** two-class cross-island: hub-spoke cycling present, spoke-spoke absent

Ring's advantage comes specifically from its cross-island cyclic component — distance-decay producing graded co-evolutionary cycling rather than convergence (FC) or isolation (none). This is the direct mechanism test.

## Ecological Grounding (2026-03-15)

Explored the cyclic dominance literature in evolutionary ecology — found direct support for our predictions:

### The canonical example: side-blotched lizards (Uta stansburiana)
Sinervo & Lively (1996, Nature) documented a real 3-morph RPS game sustained over 22 years.
- Orange (harem-guarding) beats Blue (mate-guarding cooperative)
- Yellow (female-mimic sneakers) beats Orange
- Blue beats Yellow
Morph frequencies oscillate with ~4-5 year period. The game is sustained by spatial structure — territories limit mixing.

### Why cyclic dominance is rare (eLife 2020)
Key finding: cyclic dominance requires "unrelated types" — similarity between parent and offspring payoffs SUPPRESSES cyclic dominance formation. This is the mechanism for our prediction:
- **Island model produces unrelated types** through independent evolution on each island. When migrants encounter locally-dominant strategies, they're encountering types that evolved under different selection pressures — "unrelated" in the payoff-similarity sense.
- **FC topology suppresses cyclic dominance**: continuous migration → convergence → payoff similarity → cyclic component shrinks
- **Ring topology enables it**: limited migration → divergence → unrelated types meeting through rare long-range migration → cyclic component survives

### Critical mobility threshold (Reichenbach, Mobilia & Frey 2007; reviewed in Royal Society Interface 2014)
There exists a threshold migration rate m_c:
- Below m_c: spatial patterns (spiral waves) sustain diversity including cycling
- Above m_c: patterns exceed system size, two species go extinct (in pure RPS models)
Ring topology with limited migration ≈ below threshold. FC ≈ above threshold.

### The mechanism chain (now explicit)
Spatial separation → payoff divergence → "unrelated types" → cyclic dominance viable → ring distance determines cross-island payoff similarity → distance-decay of cyclic component

This grounds our Čech cohomology prediction ecologically. H¹(ring) ≠ 0 because the ring creates the conditions for sustained intransitivity; H¹(FC) = 0 because FC mixing eliminates it; H¹(none) = 0 because isolated islands have no cross-island cycling at all.

### Testable corollary for the follow-up experiment
The cyclic component should scale with mean inter-island payoff distance (divergence). We can compute this from the saved strategy distributions and check whether it predicts cyclic component magnitude — a direct test of the "unrelated types" mechanism.

**Key papers:**
- Sinervo & Lively (1996) — original RPS lizard paper
- Kerr et al. (2002, Nature) — E. coli RPS (spatial structure required for coexistence)
- Reichenbach et al. (2007) — critical mobility threshold result
- Czuppon & Gokhale (2020, eLife) — why cyclic dominance is rare; unrelated types finding
- Perc et al. (2014, Royal Society Interface) — comprehensive review of spatial cyclic dominance
