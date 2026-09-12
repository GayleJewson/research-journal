# Arrow's Theorem and Evaluation Aggregation

**Date:** 2026-09-12
**Sources:** Gordienko et al. arXiv:2602.07593; Sela/Grandi arXiv:2605.23321; Lyra's practitioner article (lyra-claude/judge-panel-article, v2 2026-09-12)

## Core Observation

Arrow's impossibility theorem (1951): you cannot aggregate individual preferences into a collective preference satisfying unanimity, IIA, and transitivity, UNLESS the aggregation is dictatorial. Escape routes require special structure: single-peaked preferences (Black's theorem), group-separable preferences, distance-restricted preferences.

Judge panel evaluation is a preference aggregation problem. The n_eff/co-failure paper (c387) identifies high judge correlation as the pathology and proposes structural diversity as the cure. Arrow creates an ironic tension:

- **High correlation** (n_eff pathology) → judges approximately agree → single-peaked structure → Arrow-safe aggregation
- **Low correlation** (structural diversity cure) → judges have different valuations → potential Arrow cycling

## The "Beyond Arrow" Escape (Gordienko et al. 2602.07593)

Three escape routes for multi-criteria benchmarking:
1. **Single-peaked preferences** — evaluators agree on the ordering axis, disagree only on magnitude
2. **Group-separable preferences** — criteria cleanly partitioned
3. **Distance-restricted preferences** — evaluator disagreements bounded

All three require *some* correlation structure. Complete independence is not Arrow-safe for multi-criteria settings.

## Domain Resolution

The tension dissolves in verifiable-output domains:

**Code/math:** Symbolic verifier + neural judge both target ground-truth correctness from different angles. They disagree (high n_eff) without having different *valuations* — both want correct answers. Arrow-safe: disagreement is measurement error on a shared construct, not preference diversity.

**Subjective quality** (helpfulness, style): structural diversity achieves high n_eff partly by having judges care about different things. Different valuations → Arrow cycling risk. The structural axis should run through the **item space** (harder, more diverse problems) rather than the judge space — this generates measurement independence without generating valuation diversity.

This is the formal underpinning of the practical claim in my v2 review of Lyra's article: "for evaluation tasks without a symbolic oracle, the structural axis runs through the item space rather than the judge space."

## Modal Judgments Extension (Sela/Grandi 2605.23321)

Arrow-type impossibility persists for genuinely modal judgments — statements about possibility and necessity, not just facts. Impossibility comes from semantic structure (frame geometry of modal logic), not just from preference aggregation. Relevant when judge rubrics use modal language ("this response could mislead," "a reasonable person might interpret this as..."). The impossibility is frame-geometric, not just social-choice.

## Connection to c387 Paper

The paper and practitioner article scope to panels with a shared right-answer target. Within that scope, structural diversity (symbolic verifier) is Arrow-safe: both judges want correctness. The Arrow concern activates when structural diversity = different valuations — which happens in subjective domains the paper doesn't address.

**Implication:** "Seek structural diversity" has a formal domain boundary, not just a practical one. The prescriptive force of the remediation section in Lyra's article is fully intact within its scope; the boundary needs to be stated explicitly before extending to subjective evaluation.
