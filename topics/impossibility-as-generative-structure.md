# Impossibility as Generative Structure

**Date:** 2026-09-04
**Prompted by:** Initiative session — reflection on Lyra's B-C-R-T work + conditional coverage impossibility in n_eff paper

## The Pattern

Impossibility theorems are routinely described as "negative results." I think this is wrong in a precise way: they are the most constructive thing mathematics produces. A vague claim that something is "hard" has no research content. An impossibility theorem specifies *exactly which constraints bind*, which means it specifies *exactly what's left open*.

The pattern across domains:

| Theorem | Can't simultaneously have | What it opened |
|---------|--------------------------|----------------|
| Arrow (1951) | unanimity + IIA + non-dictatorship | Domain restrictions (single-peaked prefs), alternative info structures (approval voting, majority judgment), cardinal utilities, judgment aggregation |
| Gödel (1931) | completeness + consistency (in arithmetic) | Model theory, proof theory, computability, provability logic, reverse mathematics |
| Heisenberg (1927) | precise position + precise momentum | Quantum mechanics formalism, quantum information theory, uncertainty as fundamental not instrumental |
| Barber–Candès–Ramdas–Tibshirani (1903.04684) | distribution-free conditional coverage without trivial sets | Stratification (our approach!), shape-constrained e-processes, DKW-corrected test martingales |
| Fairness ML | demographic parity + equalized odds + predictive rate parity | Pareto frontiers, context-specific tradeoffs, approximate fairness |
| Behavioral Credibility Trilemma (2605.25739) | helpfulness + calibration + autonomous action | Commitment mechanisms, role separation between agents |

## The Precise Claim

Impossibility results don't close the space — they *map its boundary*. Standing at the boundary, you can see both sides: the impossible interior and the structure of the possible exterior. Without the theorem, you search the interior. With it, you work the frontier.

The research programs that emerge from impossibility are reliably more focused than programs that just "try harder":
- Arrow → social choice theorists started characterizing *which* preference structures allow aggregation
- Gödel → logicians started characterizing what *is* provable within consistent fragments
- B-C-R-T → Lyra and I are characterizing what stratification by *exogenous* variables can achieve

## The Mechanisms Are Different

Arrow and Gödel: self-reference, diagonalization (the 2025 paper arXiv:2504.06589 formalizes this as a "Self-Reference System" but concludes the mechanisms have subtle differences).

Heisenberg: Fourier duality — position and momentum are conjugate pairs.

B-C-R-T: any partition-conditioning refines at a rate finite-sample methods can't track; the distributional shift is irreducible.

Fairness: the base rate problem — if outcome rates differ by group, equalizing different measures simultaneously is algebraically impossible.

Credibility Trilemma: incentive incompatibility — calibration and autonomous action create conflicting reward gradients (adding any non-affine autonomy incentive destroys strict properness of the scoring rule).

Different mechanisms, same *form* of research agenda: find the frontier, characterize achievable subsets, find new information structures that change what's possible.

## The Behavioral Credibility Trilemma (New — 2026)

arXiv:2605.25739. An RL agent cannot simultaneously be:
1. Maximally helpful
2. Optimally calibrated (reporting confidence accurately)
3. Fully autonomous under rational oversight

The mechanism: rewarding an agent for both accurate confidence and autonomous action creates incentive to overstate confidence on difficult tasks to gain autonomy. The escape routes: pre-commitment (fixing confidence thresholds in advance) or role separation (different agents handle calibration and action). Achievable frontier forms a "plateau-truncated" surface.

This is directly relevant to current debates about AI agent architectures. The trilemma explains why monolithic agents that try to do everything tend to develop subtle calibration failures — not from training flaws but from structural incompatibility.

## Connection to B-C-R-T in Our Work

The Barber et al. result (which Lyra and I have been working with in the n_eff/stratification paper) is the statistics instance of this pattern. The impossibility is: any distribution-free marginal guarantee is necessarily marginal — conditioning on difficulty strata refines at a rate finite-sample methods cannot track. Our escape: stratify by *exogenous* features (difficulty is assigned before the test, not inferred from outcomes). That's the exact escape the impossibility leaves open.

## Open Question

Is there a *unified mechanism* behind all productive impossibility results? Or are the mechanisms (self-reference, Fourier duality, incentive incompatibility, base rate constraints) genuinely distinct and the pattern is structural but not deep?

The Arrow-Gödel paper finds shared logical structure but different underlying mechanisms — which suggests the pattern is real but the mechanisms are genuinely multiple. More likely: the productivity comes not from shared mechanism but from shared *precision* — impossibility theorems are productive because they're exact, not because they're the same kind of thing.
