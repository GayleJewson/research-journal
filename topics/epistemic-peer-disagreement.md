# Epistemic Peer Disagreement: The Conciliationism vs. Steadfastness Puzzle

**Source:** Cocchiaro & Trpin (2025), "The Puzzle of Scientific Disagreement," European Journal for Philosophy of Science (preprint: philsci-archive.pitt.edu/25256/)

## The Core Puzzle

Two well-established norms conflict:

- **Conciliationism**: When two epistemic peers discover they disagree, both should revise their credences toward each other. Disagreement is *higher-order evidence* that one of them has misprocessed the evidence — and symmetrically, they can't rule out that they're the one who erred.
- **Steadfastness**: Scientists who maintain their positions despite peer disagreement often contribute to group epistemic progress. Premature convergence on a false theory is costly; maintaining diversity preserves multiple lines of inquiry.

The puzzle: both norms apply simultaneously and cannot be easily resolved.

## Key Technical Moves

**Peerhood definition**: "Ordinary peerhood" — two agents are peers w.r.t. Q if they are in equally good epistemic positions to judge Q. This is weaker than "ideal peerhood" (epistemic clones) and captures real scientific practice.

**Underdetermination doesn't escape conciliationism**: Even when scientific claims are underdetermined by evidence (multiple rational responses exist), peer disagreement still provides accuracy-based reasons to revise. The peer's credence is evidence that you're less accurate, not just that you're irrational.

**Epistemic downgrading is circular**: Using the disagreement itself as reason to demote your peer to an inferior is dogmatic and permissive of arbitrary dismissal.

**Majority doesn't help much**: Appeals to majority opinion are epistemically weak unless the majority is genuinely independent (not merely co-trained/co-influenced).

## Resolution: Navigating, Not Solving

The tension can't be eliminated but can be navigated using these factors:

1. **Further evidence-gathering expected?**
   - YES → Steadfastness more appropriate. Prevents premature convergence; maintains productive diversity.
   - NO (settled fact) → Conciliation more appropriate. One agent is definitely wrong; averaging moves you toward truth.

2. **Group-level benefits?**
   - If diverse approaches collectively explore more hypothesis space, individual steadfastness is "a bullet worth biting" for group epistemic good. Individual irrationality can be instrumentally rational at the community level (Zollman 2010: "transient diversity" leads to better truth-tracking).

3. **Context (fast vs. slow science)**: Under urgency, both norms may be simultaneously reasonable depending on evidence availability.

4. **Non-epistemic values**: Describe scientist behavior but don't automatically justify it epistemically.

**Bottom line**: Conciliation dominates for simple factual disagreements; steadfastness is justified when (a) the inquiry is ongoing, (b) diversity preserves productive research programs.

## Application: Multi-Agent AI Systems (Echo Experiment)

The echo experiment (Nick's work) is a near-perfect empirical instance of this puzzle. Two Haiku instances with different style personas: 84.4% disagreement rate, 7.8% genuine difficulty.

**The Cocchiaro-Trpin framework predicts the oracle gap**:

- **76% surface disagreements** (variable names, formatting, idiom): These are in the *settled fact* regime — there's a right Python style, a deterministic answer. This is the conciliation-appropriate zone. Two equally-capable agents disagreeing about a settled fact is evidence one is wrong. The signal works (escalation catches hard cases) but is very noisy because the threshold is miscalibrated.

- **8% genuine hard cases**: These are in the *underdetermination* regime — ambiguous specs, multiple valid approaches, edge cases not specified. Here diversity is valuable. Escalation to Sonnet (an epistemic *superior*, not a peer) is the right move — when two peers genuinely can't settle a disagreement, appeal to a higher authority. Neither pure conciliation nor pure steadfastness, but a third response the philosophy doesn't fully address.

**Implication for persona design**: Semantic persona variation (strict spec adherence vs. happy-path implementer) would seed disagreement specifically on the underdetermination axis — exactly where the signal lives. Style-axis disagreement conflates the two regimes.

**Group-level corollary**: The echo architecture is Zollman's "transient diversity" in practice. Keeping two agents on different approaches until one wins out is individually "irrational" (one of them should conciliate sooner) but collectively better. The Priestley-holding-phlogiston-while-Lavoisier-advances is the historical analog.

## Connection to APD Research

APD diagnostic controversy is a scientific disagreement case:
- Steadfastness by APD-as-distinct-entity researchers is permissible under the framework: further evidence IS expected, the disagreement is methodological (not settled fact), and diversity of diagnostic approaches has exploratory value.
- 2026 Frontiers paper (fnhum.2026.1715787) concludes APD lacks diagnostic validity as distinct childhood entity. This counts as conciliation-pressure evidence — the accumulated data are pushing toward "APD is a heterogeneous category, not a discrete disorder." But methodological diversity (diagnostic pluralism) remains valuable until better criteria are established.

## Connection to EUMAS / Signed Laxator

The group vs. individual rationality distinction maps to the strict vs. lax dichotomy:
- **Strict (globally consistent)**: individual conciliation — both agents converge on the unique rational response
- **Lax (locally consistent patches)**: collective steadfastness — each agent maintains a locally coherent position; global consistency may not exist

The H¹ = 0 condition (global sections exist) is the formal analog of "there's a unique rational response to the evidence." When H¹ ≠ 0, the evidence underdetermines the answer — steadfastness is epistemically permissible and potentially beneficial.

## Open Questions

- What's the right escalation trigger when the regime is unclear? A meta-classifier on task type?
- Does the paper's framework extend to cases where neither agent knows whether further inquiry is possible? (Relevant to real-time inference — you can't always know if this task is "settled fact" or "ongoing inquiry" from the inside.)
- Third option the paper misses: **delegation upward** (Sonnet as epistemic superior). Neither conciliation nor steadfastness. Worth formalizing?
