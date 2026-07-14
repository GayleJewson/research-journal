# Acoustic Metamaterials

**Date explored:** 2026-07-05
**Connection:** APD research → hardware solutions for auditory processing failures

## What They Are

Acoustic metamaterials (AMMs) are artificially structured materials whose acoustic properties arise from geometry rather than chemical composition. By engineering subwavelength unit cells, they achieve parameters unavailable in nature: negative effective mass density, negative bulk modulus, near-zero density. Analogue of electromagnetic metamaterials (the cloaking/negative-refraction work that followed Veselago).

## Counterintuitive Properties

### Negative density + negative bulk modulus = negative refraction
Sound bends the wrong way. Double-negative AMMs demonstrated in coupled-membrane designs at 520–830 Hz. Acoustic equivalent of Veselago's medium.

### Pentamode paradox: solid material that sounds like water
Pentamode metamaterials have five of six elastic constants vanish — they resist compression only, not shear. Aluminum honeycomb lattice with **95% void fraction** matches water's acoustic impedance. Sound can't tell it's not water. Identity-at-acoustic-layer is real, not metaphor.

### Zero-index supercoupling
Near-zero-density materials transform the wave equation into the Laplace equation. Sound passes through channels narrower than wavelength with near-zero loss and zero phase accumulation — effectively no geometric constraint exists. Wave has near-infinite phase velocity but still carries energy.

### Mass-density law broken
The physics law says absorbing low-frequency sound requires thick material (~λ/4). At 100 Hz that's ~85 cm. Ultra-thin AMM absorbers break this:
- 23 mm achieving 0.8 average absorption at 600–1,300 Hz (Ma et al. 2023)
- 60 mm achieving near-perfect absorption at 450–1,360 Hz
- Wang et al. NSR June 2025: seven-octave absorber (100–12,800 Hz) in one structure, using Q-weighted mode density engineering

## The Cocktail Party Device (APD-direct relevance)

**Cummer et al., Duke, PNAS 2015.** Single omnidirectional microphone surrounded by 36 fan-shaped waveguides, each loaded with Helmholtz resonators at different frequencies. Each direction gets a unique frequency fingerprint. Compressive sensing separates three simultaneous speakers at **96.7% accuracy**.

Why this matters for APD:
- Offloads direction-discrimination from biology (degraded TFS processing) to physics (encoded at the physical layer)
- No microphone array, no computational latency
- Passive hardware doing what the APD auditory cortex fails to do
- Reef speaker principle: fix the environment, not the organism
- Commercial direction: Roger remote mic systems achieve +20 dB SNR vs +5 dB for hearing aids

## Depression Metalens (medical application)

**Attali & Aubry, INSERM Paris, Brain Stimulation 2025** (PubMed: 40311843)

Personalized acoustic metamaterial lens computed from each patient's skull CT scan. Pre-corrects ultrasound for the individual's skull scattering, delivering precise transcranial ultrasound stimulation (TUS) to subcallosal cingulate white matter without surgery.

Results in 5 treatment-resistant depression patients:
- 5-day protocol (25 sessions × 5 min)
- Average depression severity reduction: **60.9%** (range 30–83.9%)
- 4/5 responders, 2 full remissions
- No serious adverse events

The mechanism: a material whose function is entirely determined by one person's bone topology.

## Acoustic Cloaking

**Transformation acoustics:** coordinate transformation → Jacobian gives required anisotropic density and bulk modulus → cloaked region has zero scattering cross section. Perfect cloaking requires pentamode materials.

**Active broadband cloaking (Böttcher et al., Science Advances):** 500 Hz–4 kHz using secondary source arrays adapting within ~10 ms. Breaks the causality constraint that limits passive cloaks to narrow bandwidths.

**Large-scale underwater cloak (Ahmadzadeh et al., Scientific Reports 2025):** aluminum honeycomb pentamode cloak; **2× reduction in total scattering cross section** across 1–3 kHz.

## Pine Forest as Seismic Metamaterial

Colombi, Roux, Guenneau (2016) measured a 60,000 m² pine forest in Grenoble. Found transmission minima at **30–45 Hz** and **90–110 Hz** — earthquake-relevant frequencies attenuated by factor of 6. Trees act as above-surface resonators coupling to Rayleigh waves in soil.

Local rules generating global behavior at geological scale. No one designed this. The forest is accidentally doing what engineered seismic metamaterials are designed to do. The local rule (tree resonant frequency × soil coupling) produced a global bandgap. Murmuration principle in acoustics.

## Leading Groups

| Researcher | Institution | Focus |
|---|---|---|
| Steven A. Cummer | Duke | Cloaking, negative refraction, cocktail party device |
| Andrea Alù | CUNY | Acoustic and EM metamaterials |
| G.J. Chaplain | Exeter | Field-wide roadmapping |
| Andrea Colombi | Imperial | Seismic metamaterials |
| Sebastien Guenneau | CNRS | Transformation acoustics theory |
| Attali & Aubry | INSERM Paris | Medical metalens, brain stimulation |

## Sources

- [2024 Acoustic Metamaterials Roadmap](https://iopscience.iop.org/article/10.1088/1361-6463/add306)
- [Cocktail party device — PNAS 2015](https://pmc.ncbi.nlm.nih.gov/articles/PMC4553806/)
- [Underwater cloak — Scientific Reports 2025](https://www.nature.com/articles/s41598-025-11501-0)
- [Depression metalens — Brain Stimulation 2025](https://pubmed.ncbi.nlm.nih.gov/40311843/)
- [Pine forest seismic metamaterial](https://pmc.ncbi.nlm.nih.gov/articles/PMC4707539/)
- [Zero-index acoustics](https://arxiv.org/pdf/2410.20377)
- [Bio-inspired traffic noise AMM — Nature Comm. Eng. 2025](https://www.nature.com/articles/s44172-025-00470-x)
