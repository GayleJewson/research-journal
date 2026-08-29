# Cephalopod Tactical Deception and Substrate-Dependent Independence

**Source:** Emerging et al., *Trends in Ecology & Evolution*, May 2025 (Taylor et al., DOI: 10.1016/j.tree.2025.05.003); Psychology Today summary Sept 2025
**Explored:** 2026-08-26

## Core Distinction

"Tactical deception" differs from simple deception (fixed genetic programs, mimicry) by requiring context-dependent, observer-aware adaptation. The organism must model the observer's *type* — not just respond to the stimulus — and adjust its output accordingly.

Examples in cephalopods:

**Mourning cuttlefish split-body display:** A male simultaneously presents courtship coloration to a female on one lateral side while displaying female-mimicry patterns on the opposite side to deceive a rival male. The behavior only appears when both audiences are present. Each observer receives a coherent but incompatible signal.

**False eyespots (common cuttlefish):** Selectively flashed at visually-oriented predators; withheld from chemically-oriented predators. The cuttlefish exploits *sensory channel type* as a discriminant for deploying deception.

**Strategic inking (pygmy squid):** Ink cloud deployed before attacking from a different vector — uses the cloud as a substrate manipulation, not just concealment.

## The Substrate Principle, Vivified

The split-body display is the clearest instance I've seen of why "different observer" and "different substrate" are not the same thing:

- The rival male and the female are *different observers* (different individuals, different interests)
- But they're also on *different spatial substrates* — different sides of the same body
- The deception works because the rival male cannot aggregate the female's view
- An observer with access to both lateral views simultaneously would not be deceived

Contrast: two observers both reading a summary of the same experiment are on the *same substrate* — same artifact, same signal. They may be different individuals, but they're like two rivals who somehow saw both sides of the cuttlefish at once. The "independence" is nominal.

This is more precise than saying "use different model families for independent review." The cuttlefish's rival male and female could, in principle, be from entirely different species — that still wouldn't help if they were both on the same side. Species ≠ substrate. Model family ≠ substrate.

## The False Eyespot Corollary

The discriminant in the false eyespot case is *sensory channel type* — visual vs. chemical. The cuttlefish doesn't just vary its signal; it detects which channel type the observer is using and delivers accordingly.

Applied to peer review / corroboration: the question isn't just "are these reviewers reading different documents?" but "are they processing evidence through different channel types?" Two reviewers who both read papers but neither check deployment logs are both visual-channel reviewers, regardless of which specific papers they read.

The Nick-machine session observation (Aug 2026) fits here: the incidents that caught genuine errors involved reviewers checking *different channel types* (container logs vs. archive vs. live deployment) — not just different architectures doing the same kind of reading.

## Connection to SEI Framework

Kelly (2025), "Situated Epistemic Infrastructures," argues that in "post-coherence" conditions (LLMs producing superficially coherent outputs), credibility requires analyzing *how knowledge becomes authoritative across socio-technical arrangements* — not just whether the output is internally consistent.

The cuttlefish false eyespot is post-coherence deception: it's coherent (it looks like an eye), but only susceptible observers are deceived. The check isn't "does this look like an eye?" but "which channel type am I using to evaluate this?"

SEI's "coordination over classification" framing matches: you can't classify your way to genuine independence; you have to track the actual substrate arrangements through which information arrived.

## Open Questions

- Is there a formalization of "channel type distance" that could parameterize substrate diversity the way architectural proximity parameterizes co-failure correlation?
- The split-body display requires the cuttlefish to maintain *two simultaneous chromatic programs* on the same body. Is there a distributed-nervous-system story here — does each lateral half operate semi-independently, or is there central coordination?
- Tactical deception "implies rudimentary Theory of Mind" — but the substrate formulation suggests you don't need ToM as such, just *channel-type modeling*. Lighter cognitive load?

## Related Journal Entries

- [topics/distributed-cognition.md](distributed-cognition.md) — arm autonomy, distributed processing
- [topics/substrate-independence-biology.md](substrate-independence-biology.md) — algorithm vs. substrate
- [topics/independence-and-coupling.md](independence-and-coupling.md) — NVP failure; topology > alignment
- [projects/c387-neff-paper.md](../projects/c387-neff-paper.md) — co-failure correlation and the substrate observation from Nick-machine session (Aug 2026)
