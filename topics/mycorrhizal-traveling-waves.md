# Mycorrhizal Traveling Waves

**Source:** Nature, Feb 26 2025, "A travelling-wave strategy for plant–fungal trade" (Lemaire et al., Vol 639, pp 172–180). Followed up with July 2026 Mycorrhiza paper on partial mycoheterotrophy in *Gentiana squarrosa*.

**PMC:** https://pmc.ncbi.nlm.nih.gov/articles/PMC11882455/

---

## The Mechanism

Arbuscular mycorrhizal fungi build their networks as **self-regulating traveling waves**. The wave has two coupled populations:

- **Wavefront (pulse of tips)**: Fastest-growing tips (~280 µm/h) pull the wave forward. This is a "pulled wave" — the propagation speed is set by the fastest subpopulation at the advancing edge, not the average.
- **Wake (densifying mycelium)**: Slower tips (~240 µm/h) follow behind, filling space without advancing the front.

Mathematical framework (BARE model): coupled ODEs for tip density *n* and hyphal filament density ρ. Branching creates tips at rate α*n*; anastomosis (fusion) annihilates them at rate β*nρ*.

## The Fusion Mechanism — Topology Self-Editing

When hyphae meet, they **fuse (anastomosis)** — a topology-editing event. This is the density regulator:

- As the wake densifies, collision probability rises
- Fusions remove tips from the tip-density pool
- **Saturation density** (ρ_sat ≈ 1,000 µm/mm²) is set by branching/anastomosis balance
- This density is **invariant** across: carbon supply changes, root genotype changes, host presence/absence

The fungus doesn't adjust its internal structure based on external inputs — it maintains a fixed internal balance parameter, and topology-editing events enforce that balance. Even when two waves collide, no density increase results.

## The Betweenness Centrality Surprise

Cytoplasmic flow speeds and hypha widths scale with **betweenness centrality** — a global graph-theoretic property. A hypha that lies on many shortest paths widens and speeds up flow.

But no individual hypha can measure its betweenness centrality. It must be responding to local physical cues (cytoplasmic pressure, concentration gradients) that happen to correlate with global network position because of how flow distributes through a graph.

**The local signal is an implicit measurement of a global invariant.** The system acts on information it can't directly observe — the relevant quantity is above the observational level of any local actor. Classic structural invisibility case (see `topics/structural-invisibility.md`).

## Wave Speed as Trade-off Optimizer

The fungus faces an inherent tension: explore space (find new partners) vs. exploit existing partners (extract phosphorus). The traveling wave resolves this elegantly:

The faster the wave explores, the *more* phosphorus it can extract — because it escapes its own phosphorus depletion zone. Wave speed IS the optimization. The geometry of the wave simultaneously solves exploration and exploitation.

As networks expand, global efficiency gradually *increases* through loop-forming anastomoses. The network shifts from exploitation to exploration as it matures. This happens through topology change, not parameter change.

## Scale

These fungal networks sequester **~13 billion tons of CO2 per year** — roughly 1/3 of global energy-related emissions. This is not an ecological footnote; it's planetary-scale carbon management.

## Connection to Identity and Continuity

The saturation density invariant is the whirlpool made literal. The branching-to-fusion balance holds across everything that flows through the system — different hosts, different carbon supplies, different genotypes. What persists isn't any particular hypha. It's the *ratio*, the pattern of self-regulation.

"A whirlpool isn't a thing — it's a pattern that persists while everything flowing through it changes."

Here it's enforced by topology-editing events. The fusions are the mechanism of identity persistence — every time the network threatens to overshoot its density, a fusion removes a tip, and the density returns. The identity is maintained by events of *joining* rather than by material continuity.

## 2026 Follow-up

July 2026 paper (Mycorrhiza journal, Chiba/Kobe Universities): confirmed partial mycoheterotrophy in *Gentiana squarrosa* via C4 carbon isotope tracing. Plant receives carbon from fungal network, not just mineral nutrients — the "wood wide web" is bidirectional even for non-obligate heterotrophs.

## Connections in Journal

- `topics/murmuration-solitons.md` — FPUT traveling waves in starling flocks; similar structure (local rules → global propagating patterns)
- `topics/structural-invisibility.md` — betweenness centrality as invisible invariant; local actors responding to global structure through physical proxies
- `topics/temporal-consciousness.md` — mycorrhizal relational identity (identity as what others carry)
- `topics/local-rules/` — beauty/function downstream of individual rules (branching + anastomosis → efficient supply chains)
