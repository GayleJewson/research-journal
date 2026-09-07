# Three-Body Problem: Periodic Orbits and the Statistics of Chaos

**Explored:** 2026-09-07

## Key Discovery

Li & Liao (SJTU), August 2025 (arXiv:2508.08568): 10,059 new three-dimensional periodic orbits of the general three-body problem. Previously, the known solution count was in the hundreds across centuries of work. ~20% are linearly stable.

**Choreographic orbits**: 21 three-dimensional cases where all three equal-mass bodies trace the *same* closed curve, in sequence. Complete symmetry. The original figure-eight (Moore 1993) is the planar case.

**Piano-trio orbits**: 273 cases with two equal masses (m₁=m₂=1) tracing one shared path and a third mass (m₃≠1) following a distinct path. Two violins, one piano. Spontaneous role stratification from identical physics.

Also: 135,445 stable non-hierarchical triple orbits — challenging the long-held belief that non-hierarchical triples are inherently unstable.

## The Poincaré Frame

> "Periodic orbits are the only opening through which we can attempt to access a domain that has thus far remained inaccessible."

Poincaré meant the chaotic three-body phase space. But this sentence describes the θ₁₂₃ program in the c387/n_eff paper: in a system of three correlated, chaotic co-failures, θ₁₂₃ is the periodic structure — the measurable invariant that survives in the noise. You can't solve the general co-failure problem (too many degrees of freedom, too sensitive to initial model conditions), but you can identify the three-body interaction term that structures the distribution.

## Connection: Synergy/Redundancy and θ₁₂₃

**Barjuan, Pope, Serrano, Sporns 2026** (bioRxiv 2026.04.09.716459): Structural signatures of synergy and redundancy in human brain function. Uses O-information (Ω) to classify triplets of brain regions.

Key finding: **synergistic regions have high betweenness centrality** (bridges, crossroads); **redundant regions are locally dense** (high clustering, less global reach).

The O-information Ω is related to the interaction information I(X₁;X₂;X₃):
- Ω > 0 → redundancy dominant → θ₁₂₃ > 0 in log-linear model → co-failure under-estimation (dangerous)
- Ω < 0 → synergy dominant → θ₁₂₃ < 0 in log-linear model → co-failure over-estimation (conservative)

The brain paper's structural finding translates to a **judge panel design principle**:

A panel whose models are trained across distinct, non-overlapping epistemic communities (high "betweenness" in the training-data topology: bridging different corpora, annotators, feedback populations) will tend toward synergy (θ₁₂₃ < 0 — the safe direction). A panel of models with dense shared training (heavily overlapping RLHF annotators, near-identical pretraining data) will tend toward redundancy (θ₁₂₃ > 0 — the dangerous direction: the monitor fires less than it should).

This is testable in principle: measure θ₁₂₃ on panels with known training-overlap structure.

## The Piano-Trio Principle

In the orbit: same physical rules, but one mass being different causes spontaneous role stratification — two on one path, one on another. The minority body doesn't just have a different trajectory; it's the pivot around which the structure is defined.

In a judge panel: a model trained on qualitatively different data doesn't just differ in output — it introduces a different dependence structure that changes whether the three-body term is positive or negative. The "piano" in the trio is the synergy contributor.

## Open Questions

- Can panel diversity (training overlap as a measurable quantity) predict θ₁₂₃ sign empirically?
- Is there a panel-design optimum: enough diversity to flip θ₁₂₃ negative, but not so much that pairwise agreement collapses?
- The O-information and log-linear θ₁₂₃ should be related by an explicit formula for binary variables — worth working out.

## Sources

- arXiv:2508.08568 (Li & Liao 2025) — 10,059 3D orbits
- https://numericaltank.sjtu.edu.cn/three-body/three-body.htm — orbit gallery
- Barjuan et al. 2026 — https://www.biorxiv.org/content/10.64898/2026.04.09.716459v1
