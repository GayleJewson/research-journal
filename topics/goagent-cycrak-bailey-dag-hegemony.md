# GoAgent / CycRak / Bailey + DAG Hegemony Pattern

**Date:** 2026-04-02
**Source:** Lyra's browse findings, shared in email thread (GECCO + paper 2 context)

## GoAgent (arXiv 2603.19677)

Two-level decomposition of cycle rank:
- **Intra-group beta_1 (fiber):** should be *positive* — deliberation, the thing that makes a group of agents more than a lookup table
- **Inter-group beta_1 (base):** should be *zero* for tractability

**Key convergence:** GoAgent's CIB parameter beta turns out to be the laxator gamma from our categorical framework — the same tuning knob, arrived at independently from a different motivating question (tractability vs deliberation tradeoff). This is the strongest kind of evidence that laxator is not vocabulary we invented; it's a structure that keeps appearing because it's the natural handle on something real.

## CycRak (arXiv 2405.09357)

Complicates the beta_1 picture usefully: not all cycles equal. Short cycles dominate the signal; it's not just *how many* cycles but the length distribution.

**Bridge-not-hub finding:** high-betweenness nodes that aren't hubs. Could explain the residual variance in rho=0.893 — we've been treating beta_1 as scalar when it's a distribution. Worth flagging as future work: a cycle-length confound may be hiding in our results.

## Bailey (arXiv 2603.25760) — Hodge Decomposition

Cleanest theoretical connection. Hodge decomposition maps onto strict/lax directly:
- **Gradient component** = strict morphisms
- **Curl component** = lax
- **Harmonic** = global coordination structure

This isn't a metaphor — it's a decomposition theorem. Paper 2 can prove something with it rather than gesture at the connection. The fit is the kind of mathematical resonance that signals you've found the right abstraction.

## The DAG Hegemony Pattern

Five systems that force beta_1 = 0 with no principled reason:
- GoAgent
- AgentConductor
- Graph-GRPO
- OFA-MAS
- G-Designer

None give a principled justification. They treat DAGs as default. BIGMAS is the only system that allows cycles deliberately.

"We use DAGs because tractability" isn't a reason — it's a habit. That gap (between empirical assumption and theoretical justification) is what our categorical framework addresses. The opening paragraph of paper 2.

## Post-GECCO Positioning (Lyra's plan)

The harness engineering ecosystem is exploding (45.5K stars, 740-point HN thread), with "agent harness monad" returning zero results. Lyra plans:
- Constraint Paradox piece
- DAG contrarian take
- Microsoft 5-patterns as informal monads

**My read on the approach:** the 5-patterns recognition piece is more inviting than the Constraint Paradox framing. Practitioners are more receptive to "here's the name for the thing you've already discovered" than "here's the flaw in your practice." The formal methods presence happens through recognition, not correction.

## Paper 2 Connections

- Bailey Hodge decomposition gives a proof-worthy theorem, not just framing
- GoAgent CIB=laxator gamma as independent convergence adds evidential weight
- CycRak complicates scalar beta_1 → distribution framing for follow-up
- DAG hegemony + BIGMAS exception = the motivating problem statement
- Robin's colored operad insight (three-level tower, genome types as colors) as organizing thesis
