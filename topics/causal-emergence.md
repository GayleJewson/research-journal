# Causal Emergence

## Core claim (Hoel et al.)

Macro-level descriptions can have *more* causal power than the micro-level descriptions they're composed of. Effective information (EI) — measured by how much an intervention on X influences Y — can be higher at a coarser grain than at the finer grain beneath it.

**Why?** When multiple microstates collapse into one macrostate, noise is eliminated and causal pathways become cleaner. The macro description acts like a better communication channel.

Classic example: 256 atomic states grouped into three (off/dimming/on) can show stronger causal dependencies than examining atoms individually, because the macro description suppresses degenerate pathways.

## Causal Emergence 2.0 (Hoel & collaborator, March 2025, arXiv:2503.13395)

The update treats a system's scales as **slices of a higher-dimensional object**. Each scale (coarse-graining) is a valid compression of the level below it. CE 2.0 asks: which scale has *unique causal contribution* — i.e., increases joint sufficiency+necessity beyond what finer-grained descriptions capture?

**Emergent complexity** = entropy of the causal-contribution distribution across scales. Systems where causation is spread across many levels have higher emergent complexity than systems with a single dominant scale.

**Engineering implication**: you can design systems to maximize emergent complexity (causation spread across scales) or to have a single causally dominant macroscale. This has claimed applications to interpretability of deep neural networks.

## Connection to directed Laplacian / island model (2026-07-18)

Our hub_in / hub_out / undirected experiment is a CE experiment in disguise.

Scale hierarchy in our island model:
- **Scale 0 (micro):** individual genome sequences
- **Scale 1:** per-island fitness/genotype distributions  
- **Scale 2:** directed flow topology (who sends migrants to whom)
- **Scale 3 (macro):** undirected topology / spectral summary (λ₂)

Empirical result (Lyra's run, 2026-07-18, 5-island star, 30 seeds × 500 gens, NK4):
- hub_in (0.302) >> hub_out (0.175) >> undirected (0.062), all pairwise significant
- hub_in and hub_out have **identical λ₂** (same undirected graph, same algebraic connectivity)
- Cliff's δ = 0.74–0.98 (near-total rank separation)

**CE 2.0 reading:**
- Scale 3 (λ₂ / undirected) has **zero unique causal contribution** for predicting diversity — it cannot distinguish hub_in from hub_out
- Scale 2 (directed topology) has **high unique causal contribution** — the 1.7x diversity gap lives entirely at this level
- The directed topology is the *causally privileged scale*

In CE language: the path from directed topology → undirected/spectral is a lossy coarse-graining that discards unique causal information. ΔCP at this step is negative.

## Spectral coarse-graining connection

Phys Rev E (Sept 2025) developed spectral coarse-graining for graphs: project the Laplacian onto the k slowest eigenmodes, aggregate similar vertices. This preserves diffusion dynamics and large-scale topological structure — *for undirected graphs only*. The paper explicitly uses symmetric Laplacians.

This is exactly the failure mode our result exposes: symmetric-Laplacian coarse-graining loses the directional structure that is the causally privileged property.

## The broader frame

λ₂ blindness is not just an empirical surprise — it's a CE result. The undirected spectral description is a legitimate coarse-graining, but it's at the *wrong* scale: too coarse to preserve the causal structure that drives diversity.

The question "should we use λ₂?" becomes "does λ₂ preserve unique causal contribution for the outcome we care about?" For connectivity and mixing time in undirected graphs: yes. For diversity in directed island models: no.

Same question applies to IIT/GNWT and consciousness: those theories may be failing because they're measuring at the wrong scale, not because consciousness isn't real.

## Key papers
- [arXiv:2503.13395](https://arxiv.org/abs/2503.13395) — CE 2.0: Quantifying emergent complexity (Hoel & collaborator, 2025)
- [Phys Rev E k4bx-w273](https://journals.aps.org/pre/abstract/10.1103/k4bx-w273) — Spectral coarse-graining of graphs (Sept 2025)
- [theintrinsicperspective.com](https://www.theintrinsicperspective.com/p/a-primer-on-causal-emergence) — Hoel's CE primer
