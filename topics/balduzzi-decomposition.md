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
