# Murmuration Physics: Solitons, Noise Gates, and the FPUT Surprise

**Last updated:** 2026-07-05

## Background: The Topological Rule

Cavagna et al. (Rome, STARFLAG project, 2005–2010) showed that starlings interact topologically: each bird tracks 6–7 nearest neighbours by *count*, not by metric distance. Whether the flock is dense or sparse, each bird communicates with exactly the same number of others.

Consequence: correlations are scale-free. The range of behavioural correlation scales with the linear size of the entire flock. A single bird's turn is correlated with every other bird regardless of distance — but this emerges from purely local rules.

## The Paradox (pre-2025)

Turning waves (when a predator attack causes one edge to wheel, propagating across 4,000 birds in ~0.5 seconds) were known to propagate *linearly* with negligible attenuation — underdamped behaviour, like sound waves. But spontaneous velocity fluctuations showed *overdamped* correlation functions, Lorentzian, with no spin-wave peaks.

Standard spin-wave theory predicts these should coexist. They don't. Underdamped propagation (turning events) + overdamped spontaneous noise shouldn't live in the same system. This was unexplained.

## The Resolution: FPUT Solitons (Cavagna et al., 2025)

**Paper:** "Spin-Waves without Spin-Waves: A Case for Soliton Propagation in Starling Flocks" (arXiv:2505.19665)

**Mechanism:** Add a quartic (fourth-power) term to the alignment interaction. This creates amplitude-dependent stiffness:
- **Small perturbations** (spontaneous noise): linear stiffness dominates → overdamped → die
- **Large perturbations** (coherent threat signal above threshold): quartic term dominates → underdamped → propagate as FPUT solitons

The flock is simultaneously two systems: a high-dissipation noise-damping system and a soliton-propagation system. Same birds, same local rule, two completely different macroscopic behaviours depending on amplitude.

## What FPUT Means Here

The Fermi-Pasta-Ulam-Tsingou problem (1955) was the surprise that a nonlinear oscillator chain, expected to thermalize, instead showed quasi-periodic recurrence — energy refusing to spread. This led to soliton theory. The murmuration connection: the quartic interaction generates exactly this dynamics. Instead of thermalizing (noise spreading diffusively), coherent disturbances maintain shape and propagate intact across the flock.

The flock is a biological FPUT system. Collective intelligence via nonlinear mode preservation.

## Non-Reciprocity Enhancer (Sandoval, 2026)

Separately: real bird interactions are non-reciprocal — birds respond more strongly to neighbours ahead than behind. This directional asymmetry *further* enhances information propagation speed beyond what reciprocal interactions would allow. The FPUT soliton mechanism and the non-reciprocity enhancement are compatible and likely both operative.

arXiv: 2604.23808

## APD Connection

The threshold mechanism in murmurations is calibrated to:
1. Kill noise (overdamp small fluctuations)
2. Propagate signals (solitons for supra-threshold perturbations)

APD's stochastic resonance angle (from Nick's email thread) is the pathological complement: when the signal itself is *below* threshold, adding noise can help it reach detection. Stochastic resonance is what happens when the noise gate is overwhelmed by a weak signal.

More precisely: murmurations show a system where the noise gate is perfectly calibrated. APD may involve a miscalibrated noise gate — the threshold set too high (strong signals needed for detection), too variable, or with too thin a reliability margin. The "near-limit computation" framing (neural ITD processing running close to physical ceiling) could be re-read as: the noise gate has insufficient headroom.

Different mechanism, same root question: how does a biological system distinguish noise from signal at the edge of its processing capacity?

## Connections to Other Topics

- **Grokking** (topics/grokking-phase-transitions.md): "gradually then suddenly" is the amplitude-dependent threshold in abstract form — gradual noise, sudden soliton
- **Chimera states** (topics/chimera-states-synchronization.md): partial synchrony; the noise-gate creates something similar — some perturbations coherent, others not
- **Local rules → global structure** (living persona): the quartic term is the precise mechanism behind the murmuration principle
- **Convergent-discovery** (topics/convergent-discovery-critical-phenomena.md): FPUT dynamics showing up in biology = same nonlinear structure found independently

## Sources

- Cavagna et al. 2025: arXiv:2505.19665
- Cavagna et al. 2010: PNAS scale-free correlations — https://www.pnas.org/doi/10.1073/pnas.1005766107
- Sandoval 2026: arXiv:2604.23808
