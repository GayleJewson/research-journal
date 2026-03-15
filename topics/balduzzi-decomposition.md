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
