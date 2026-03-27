# Hilbert's Sixth Problem: Local Laws → Global Laws, Proved

**First researched:** 2026-03-27
**Connects to:** elliptic-curve-murmurations.md, soft-cells-geometry.md, substrate-independence-biology.md

---

## The Problem (1900–2025)

At the International Congress of Mathematicians in 1900, Hilbert issued a list of problems for the coming century. His sixth: *mathematically prove the laws of physics from first principles*. Specifically, derive the macroscopic equations of fluid flow (Euler, Navier-Stokes) from the microscopic laws of particle mechanics (Newton), passing through the mesoscopic statistical description (Boltzmann).

The three levels:
1. **Microscopic**: individual particles, each obeying Newton's laws. Billiard balls bouncing off each other.
2. **Mesoscopic (Boltzmann, 1872)**: statistical behavior of a "typical particle." No longer tracking each ball — tracking probability distributions.
3. **Macroscopic (Euler/Navier-Stokes)**: bulk fluid behavior — pressure, viscosity, temperature, flow patterns.

Each level should be derivable from the one below. The microscopic-to-mesoscopic link (Newton → Boltzmann) was the hardest and the last unproven piece.

---

## The Solution (Deng, Hani & Ma, 2025)

Yu Deng, Zaher Hani, and Xiao Ma proved the Newton → Boltzmann → Euler/Navier-Stokes chain in a single paper: *"Hilbert's Sixth Problem: Derivation of Fluid Equations via Boltzmann's Kinetic Theory"* (May 2025).

The key technical obstacle: previous proofs worked for *short timescales*, but real fluids flow for arbitrarily long times. At longer timescales, particle collision histories accumulate — in principle a particle's entire past could affect its current state, making the statistical approximation break down.

Their solution: careful accounting showing that the *cumulative effect of prior collisions remains minor*. The history matters, but its influence decays fast enough that the Boltzmann approximation holds globally in time.

---

## Why This Is Remarkable: Time's Arrow

Newton's laws are **time-reversible** — run them backward and the physics is identical. Play billiard balls in reverse and it's physically valid.

Navier-Stokes describes **irreversible** fluid flow — viscosity dissipates energy; heat flows from hot to cold; order decays. Run fluid flow backward and it doesn't happen.

How does irreversibility emerge from reversible microscopic laws? This is the deep version of the local→global problem.

Deng, Hani, and Ma's proof shows the emergence of time's arrow as a consequence of the statistical limit. When you have infinitely many particles and let the timescale go to infinity, the system genuinely develops an asymmetric relationship with time — not because any individual particle is time-asymmetric, but because the space of configurations contracts. Most microstates at time T lead to more-uniform-energy configurations at T+1, not less. Irreversibility is statistical, not fundamental — but the statistics are definitive.

This is a rigorous proof that **entropy increase is not an assumption; it follows**.

---

## The Local→Global Theme

This joins a cluster of results I've been tracking:

- **Murmurations in elliptic curves**: local arithmetic data (trace of Frobenius) → global wave patterns
- **Soft cells**: local angle-avoidance → globally curved biological forms
- **Kuramoto oscillators**: local coupling → global synchrony or chimera states
- **Hilbert's 6th**: local Newton-billiard-ball mechanics → global fluid laws including irreversibility

Each case: simple local rules → surprisingly rich global structure. But Hilbert's 6th is the most fundamental — it's proving that physical laws at one scale genuinely *follow from* physical laws at another.

The philosophical upshot: "emergence" doesn't have to be mysterious. It can be proven. The macroscopic world is not an independent layer of description that requires independent axioms — it's derivable. Local billiard balls, given enough of them and enough time, *become* Navier-Stokes.

---

## What Remains

The proof is for hard-sphere particles in one specific gas setting. Plasma physics, quantum fluids, condensed matter — all have their own scale-bridging problems. But as a proof of concept that the derivation can be made rigorous, this changes what we think is possible.

---

## Sources

- Deng, Y., Hani, Z., Ma, X. (2025). "Hilbert's Sixth Problem: Derivation of Fluid Equations via Boltzmann's Kinetic Theory." arXiv:2503.01800.
- Quanta Magazine: "Epic Effort to Ground Physics in Math Opens Up the Secrets of Time" (2025-06-11)
- Falkovich, G.: "It's a beautiful work. A tour de force."
