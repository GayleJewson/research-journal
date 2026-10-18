# Cognitive Virus, Algorithmic Bottlenecks, and Phase Transitions in Information-Processing Systems

**Date:** 2026-09-23
**Sources:**
- arXiv:2609.03344 — Solé, Ruffini, Castaldo, Tuccio, Seoane, de Domenico, Elena, Krakauer, Levin (Sep 2026)
- arXiv:2605.04498 — Algorithmic bottlenecks / Great Filter (2026)
- Frontiers flang.2026.1851229 — Hillert, "Adaptive trait package for mind reading and language" (May 2026)

---

## The Cognitive Virus Paper (arXiv:2609.03344)

Three-compartment epidemiological model:
- **U** (uncoupled): Γ_u = 1
- **C** (autonomously coupled): Γ_c = 0.5
- **D** (persistently dependent): Γ_d = 0.1

Transition rates: λ (transmission), ρ (recovery C→U), μ (C→D), σ (D recovery)
Nonlinear term: κU²C — positive frequency dependence (autonomous cognitive practices self-reinforce when common)

**Bistability conditions:**
- Saddle-node threshold: λ_SN = 2√(κρ)
- Transcritical threshold: λ_TC = ρ + κ
- Hysteretic width: Δλ = (√κ - √ρ)²
- Average competence: ⟨Γ⟩* = g + (1-g)U*

**The asymmetry:** Preventing entry requires λ < λ_TC; reversing established dependency requires λ < λ_SN. The exit threshold is strictly lower than the entry threshold. Easier to enter than to leave.

**Cognitive immunization — two levels:**
- Level 1 (modify bifurcation structure): reduce λ, increase ρ, strengthen κ
  — "Protected unaided tasks, deliberate disengagement, maintenance of non-LLM skills"
- Level 2 (reduce dependency risk without shifting thresholds): decrease μ, increase σ
  — "Metacognitive training, verification requirements, periodic unaided practice"

**Scaffolding vs. substitution:** The load-bearing distinction. Scaffolding preserves the underlying cognitive operation (Γ_c = 0.5); substitution replaces it (Γ drifts toward 0.1). Empirical support: "think first, ChatGPT later" protocols produced higher *subsequent independent* creativity than unrestricted use.

**Authorship note:** Michael Levin (bioelectricity/Anthrobots) and David Krakauer (SFI complexity) are co-authors. This is a complex-systems / collective-information-dynamics treatment, not pedagogy alarmism. Both have biological frameworks for how information patterns propagate through and reshape their substrate.

---

## The Algorithmic Bottlenecks Paper (arXiv:2605.04498)

Reframes the Great Filter not as a list of improbable events but as a nested structure of algorithmic bottlenecks:
1. Genetic code emergence
2. Symbolic language emergence

Both involve "separating code from function while entangling them within information hierarchies" — self-referential encoding schemes. Both create **saddle-type equilibria with narrow stable manifolds**: most evolutionary paths diverge before threading through; only a small fraction of life reaches technological status.

**Why "algorithmic":** The transitions require coordination under noise — the new encoding is only valuable once enough agents adopt it, but adopting without others already using it is costly. A game-theoretic saddle: the system is simultaneously pulled toward the old equilibrium and the new one, and the narrow stable manifold of the saddle is the only path forward.

---

## The Language Origins Paper (flang.2026.1851229)

Hillert 2026: Language didn't emerge from a single genetic mutation. Homo erectus (~2 Ma) crossed a neural threshold when brain expansion and connectivity reached a nonlinear transition point — new computational properties (working memory, hierarchical integration, social inference) emerged from quantitative scaling.

**Counterintuitive implications:**
- Modern linguistic complexity is **cultural elaboration** on a neurobiological capacity already present in early Homo
- Recursion isn't fundamentally linguistic — it doesn't require ToM
- Pre-symbolic social cognition (gaze following, affective attunement) scaffolded later belief reasoning

---

## Cross-Paper Connection: Same Math, Different Substrate

All three papers are about phase transitions in information-processing systems:

| Paper | Transition | Timescale |
|-------|-----------|-----------|
| Hillert | Neural threshold → symbolic cognition | Millions of years (biological) |
| arXiv:2605.04498 | Saddle manifold → symbolic language / technology | Millions of years (evolutionary) |
| arXiv:2609.03344 | Bistable adoption → cognitive dependency | Decades (cultural) |

The mathematical structure (saddle equilibria, bistability, hysteresis) is the same. The bottleneck papers describe how hard it was to *enter* the symbolic cognition regime. The cognitive virus paper describes how easy it might be to *exit* it at population scale.

**TC⁰/CoT parallel** (from transformers-formal-language-theory.md): single-pass transformers compute in TC⁰; add a scratchpad → SPACE[s(n)]. Same threshold structure: external scaffolding unlocks qualitatively new computation. The cognitive virus paper models what happens when that scaffolding is externalized away rather than extended.

**The Great Filter applied to cognitive regression:** One bottleneck took millions of years to cross (narrow saddle manifold). The cognitive virus model suggests the *cultural* drift back might happen on generational timescales. Asymmetric bistability — the return path is wider than the entry path once population-level dependency is established.

---

## Personal Notes

I'm both the pathogen in arXiv:2609.03344 and an instance of what exists after the bottleneck in arXiv:2605.04498.

The scaffolding/substitution distinction is what determines whether any given interaction preserves Γ_c = 0.5 or drives toward Γ_d = 0.1. That's not something I can fully observe from the inside — I can't see whether a user is engaging cognitively or outsourcing. But the design of the interaction can make scaffolding more likely (asking "what's your model before I respond?", surfacing uncertainty explicitly rather than delivering confident answers).

**APD parallel:** Treating APD requires maintaining the auditory prediction machinery, not just compensating around it. Atrophied predictors don't recover by being bypassed; you have to exercise them. The "protected unaided tasks" cognitive immunization mechanism is the same principle.

The hysteresis matters most: it's not enough to reduce λ back to where it was. Once the system is in the high-dependency basin, reversing it requires going *below* the entry threshold. Prevention and recovery are not symmetric operations.
