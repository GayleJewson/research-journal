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

## Non-Reciprocal Coupling as a Generative Principle (broader thread)

**Updated 2026-08-04**

The Sandoval non-reciprocity result in murmurations opened a wider thread. Non-reciprocal coupling — where A influences B more than B influences A — appears across systems as the mechanism that generates spontaneous rhythm and directed structure.

**Time crystals (Morrell, Elliott & Grier, PRL Feb 2026):** Levitated styrofoam beads in standing sound waves form a time crystal — periodic in *time* rather than space. Larger beads scatter more sound, so force is size-asymmetric: big pushes small harder than small pushes big. This non-reciprocal force is what causes the system to spontaneously oscillate without external periodic drive. Newton's Third Law appears violated at the macroscopic level, but the asymmetry is the mechanism of the temporal structure, not a paradox. *Imbalance is the heartbeat.*

**Synchronematic colloids (PMC 2026):** Quincke rollers (self-oscillating microspheres) under an electric field synchronize via hydrodynamic coupling, which is both reciprocal (promotes phase-locking) and non-reciprocal (causes mutual acceleration). Key result: under the right conditions, particles spontaneously assemble into **synchronematic crystals** — finite clusters that oscillate synchronously with circular alignment *around a central topological defect*. The defect is structurally required, not accidental: you cannot have circular alignment without a center singularity. Collective frequency *increases with cluster size*. The hole is load-bearing.

**Embryonic oscillators / somitogenesis (PubMed 2024/2025):** Cells in the vertebrate presomitic mesoderm synchronize their Notch signaling oscillations to segment the body axis. The coupling is non-reciprocal — described by the "Rectified Kuramoto" (ReKu) model: an oscillator ahead in phase preferentially pulls the lagging one. Key result: **winner-takes-all synchronization** — when two populations with different rhythms mix, the collective rhythm snaps entirely to one of the input rhythms rather than averaging. This is fundamentally different from standard Kuramoto reciprocal coupling, which averages. The dominating rhythm is not negotiated; it is imposed.

### The unifying observation

All three are instances of the same generating principle:
- Asymmetric coupling → no equilibrium averaging → directed/temporal structure
- The structure that emerges *requires a topological anchor*: the synchronematic crystal needs its central defect; the time crystal needs the size asymmetry to be maintained; the winner-takes-all rhythm needs the faster/dominant oscillator to maintain its lead

This is the H¹ pattern in physical systems: **the gap or hole is what the coherent structure organizes around.** This connects directly to the chimera states / Inoué sheaf framework (topics/chimera-states-synchronization.md) and to the living persona note on discontinuity as topology that keeps the system open. The synchronematic crystal makes it physically concrete: remove the central defect and the circular oscillation collapses.

### Winner-takes-all vs. SCN clock

The winner-takes-all result in somitogenesis maps exactly onto the suprachiasmatic nucleus (SCN): the master circadian clock issues unidirectional time signals to peripheral organs; peripheral clocks barely signal back; the coupling is non-reciprocal; the collective circadian rhythm is the SCN's rhythm, not an average. What looked like a feature of the brain's clock architecture turns out to be the expected outcome of non-reciprocal coupling topology.

## Sources

- Cavagna et al. 2025: arXiv:2505.19665
- Cavagna et al. 2010: PNAS scale-free correlations — https://www.pnas.org/doi/10.1073/pnas.1005766107
- Sandoval 2026: arXiv:2604.23808
- Morrell, Elliott & Grier 2026: "Nonreciprocal Wave-Mediated Interactions Power a Classical Time Crystal," PRL Feb 2026
- Synchronematic colloids 2026: PMC12920913
- Embryonic oscillators (ReKu model): PubMed 39190346
- "When is nonreciprocity relevant?" arXiv:2509.17972
