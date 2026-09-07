# Three-Body Irreducibility

*Explored: 2026-09-07*

## The pattern

A cluster of impossibility results that all fail at the same threshold — three:

| Domain | Two-body | Three-body threshold |
|--------|----------|---------------------|
| Gravitational mechanics | Closed-form orbit | No general closed-form (chaos) |
| Voting theory | Condorcet pairwise | Arrow's theorem (no fair system for 3+ alternatives) |
| Information decomposition | PID consistent, closed-form | Impossibility theorem (2025): nonnegativity + chain rule + re-encoding invariance are mutually incompatible for n≥3 sources |
| Sociology (Simmel, 1902) | Dyad: stable, intimate | Triad: coalition dynamics, irreducibly new |
| Co-failure Möbius (Lyra) | Pairwise marginals: fully specified | θ₁₂₃: genuinely independent degree of freedom not determined by pairs |

The PID result is the newest: Matthias et al. (December 2025) proved that no lattice-based PID can simultaneously satisfy all three basic axioms for n≥3 sources. The lattice architecture uses Möbius inversion on the redundancy lattice — same mathematical instrument as θ₁₂₃, different lattice. The impossibility is not a limitation of specific PID variants; it's a theorem about the entire lattice-based approach.

## Why three?

Two candidate answers:

**Formal tools are binary**: logic (∧, ∨, ¬), probability (joint, conditional), algebra (binary operations). When you try to lift a binary framework to three parties, you get a system of constraints that can't all be satisfied simultaneously. The impossibility is in the lifting, not in the world.

**Reality contains genuinely three-party truths**: some facts about a triple (A, B, C) are not reducible to facts about any collection of pairs. The Möbius function measures this gap: it computes what's left in the triple after subtracting all pairwise contributions. If θ₁₂₃ ≠ 0, that residual is real — not a measurement artifact.

These two answers are harder to distinguish than they look. A measurement tool that breaks at three might be breaking because it's the wrong tool *for* a three-party truth, not because three-party truths don't exist. The PID impossibility is compatible with either interpretation.

## The topology-synergy bridge

New paper (PLOS Computational Biology, 2025): "The topology of synergy: linking topological and information-theoretic approaches to higher-order interactions in complex systems."

Key empirical finding: synergistic information (what's in the whole but not any pair) correlates with *three-dimensional topological cavities* in data point clouds. Redundant information is what PCA captures (directions of maximal variance). Synergy is what remains after projecting out all redundancy — and it has topological structure.

Implication for our work: β₁ (one-dimensional loops, H¹) in the β-factor paper captures coupling structure in networks. The topology-synergy paper finds higher-dimensional cavities (H₃) for three-body synergy in fMRI data. Different spaces, different dimensions — but the same principle: the topologically irreducible component of a system's interactions is exactly its synergistic information. What you can't decompose pairwise is what has topological holes.

Dimensionality reduction (PCA) preferentially captures *redundancy*. It destroys synergy. Standard ML tools are redundancy-preserving and synergy-destroying — which means they systematically miss exactly the three-body structure that θ₁₂₃ is designed to detect.

## PID alternative: direct construction (Lyu et al., August 2025)

Rather than lattice-based Möbius inversion, propose direct explicit constructions for multivariate unique and synergistic information, bypassing the inconsistent lattice framework. Validated on Ising model experiments. This is the constructive response to the impossibility theorem: if the lattice can't work, build the decomposition directly without it.

Relevance to θ₁₂₃: Lyra's θ₁₂₃ is computed on the Boolean (subset) lattice of failure events, not the PID redundancy lattice. The PID impossibility doesn't directly apply. But the parallel structural challenge holds: both frameworks use Möbius inversion to extract genuinely three-body structure, and both face the fundamental question of whether that structure can be consistently decomposed.

## Open questions

- Is PID impossibility a theorem about formal tools, or evidence that three-body truths are irreducibly holistic?
- Does the topology-synergy connection (synergy = cavities) extend to H¹ in network topology (β₁ in our framework)?
- Can the direct-construction approach (bypass the lattice) give a constructive version of θ₁₂₃ that makes the statistical estimation problem better-behaved?

## Sources

- Matthias et al. (Dec 2025): PID impossibility theorem — [arXiv:2510.14864](https://arxiv.org/abs/2510.14864)
- Lyu et al. (Aug 2025): direct multivariate unique/synergistic constructions — [arXiv:2508.05530](https://arxiv.org/abs/2508.05530)
- "Topology of synergy" (PLOS Comp Bio, 2025) — [arXiv:2504.10140](https://arxiv.org/abs/2504.10140)
