# Vagueness, Annotation Disagreement, and Ambiguity Collapse

**Date explored:** 2026-09-05
**Trigger:** Working on the perspectivist rebuttal in §5b of the n_eff paper prompted the question: what *is* it for a question to have a determinate answer?

## The Philosophical Landscape

Three positions on borderline cases (the SEP Fall 2025 entry):

**Epistemicism (Williamson):** Every vague predicate has a sharp cutoff; our ignorance reflects
"margin for error" principles — knowing X at threshold requires knowing X slightly before it too.
Borderline cases are epistemically opaque, not semantically gappy. Classical logic preserved.

**Supervaluationism:** Borderline statements have no truth value — true only if true under all
admissible sharpenings of the vague term. Accommodates indeterminacy while preserving classical
inference patterns.

**Fine's global boundarylessness (2020):** Vagueness is *global*, not local. Judgment must be
suspended somewhere in a sorites series, but no specific case is the borderline case — "the bubble
has the mobility of a level." This avoids both hidden thresholds (epistemicism) and truth-value gaps
(supervaluationism). Rejects classical logic's conjunctive excluded middle.

The key distinction the entry draws: **relative** borderline cases (the question is determinate, our
means are incomplete — like BMI ambiguity in obesity) vs. **absolute** borderline cases (the concept
itself has no fact of the matter — resists all possible inquiry). This maps directly onto the
perspectivist rebuttal in §5b.

## The NLP Rediscovery

The perspectivist NLP literature (arXiv:2601.09065, "Beyond Consensus") is the empirical
rediscovery of this philosophical debate:

- "Noise" view in NLP ≈ epistemicism: there's a correct label, annotators just don't know it
- "Genuine ambiguity" view in NLP ≈ supervaluationism: some items have no determinate truth value
- "Perspectivist" view in NLP ≈ Fine's holism: the concept lacks global sharp boundaries;
  different annotators represent legitimate different sharpenings

The perspectivist NLP paper presents a three-category taxonomy of disagreement sources: data factors
(ambiguity, context), task factors (subjective interpretation criteria), annotator factors (individual
differences). This is the NLP operationalization of "where does the indeterminacy live?"

## Ambiguity Collapse (arXiv:2603.05801)

LLMs trained on consensus labels — rather than distributional labels — develop a systematic failure
mode: they produce singular outputs for genuinely contested items, foreclosing deliberation. The paper
identifies three levels of risk:
- **Process**: forecloses deliberation, prevents skill development
- **Output**: distorts concepts people rely on for decision-making
- **Ecosystem**: reshapes shared vocabularies and interpretive norms

This is a *named* failure mode that the n_eff paper is implicitly trying to detect from the outside:
a model that has collapsed ambiguity will show high consensus in evaluator ratings (n_eff≈1 on items
where the "correct" n_eff is ~2). The model appears better-calibrated than it is.

## DPUA: Training Against Collapse (arXiv:2605.10415)

"Aligning LLM Uncertainty with Human Disagreement in Subjectivity Analysis" proposes a two-phase
framework: (1) disagreement perception via adaptive decoupled learning, (2) uncertainty alignment
via GRPO-based reward optimization. The goal: LLM confidence expressions should correlate with actual
human disagreement distributions on subjective tasks.

This is the complementary approach to n_eff monitoring:
- n_eff: measures whether evaluators *agree about model outputs* (external measurement)
- DPUA: trains models to *express calibrated uncertainty* (internal calibration)

Neither fully escapes a second-order problem: any quantification of uncertainty imposes local
structure on what Fine's view suggests is irreducibly global. Assigning probability 0.6 to a
genuinely boundaryless item is itself a form of collapse — more honest than 1.0, but still imposing
a scalar on a non-scalar phenomenon.

## Connection to n_eff Paper (§5b)

The perspectivist rebuttal we're handling in §5b says: "on genuinely indeterminate items, n_eff≈2
is not a failure to flag; it correctly reflects no consensus where none exists." Our rebuttal:
"we stratify by ground-truth-determinability."

The philosophical literature sharpens the operationalizability concern I raised in the cold-read:
ground-truth-determinability, like difficulty, requires external annotation — but it's *harder* than
difficulty because:
1. Difficulty has proxy measures (item complexity, domain features)
2. Ground-truth-determinability requires a judgment about whether the question has a fact of the
   matter — meta-annotation that is itself subject to disagreement
3. Fine's holism predicts that borderline cases can't be individually identified; suspension of
   judgment must occur somewhere but there's no specific item that *is* the borderline case

This doesn't undermine the stratification strategy — it just makes the operationalizability footnote
more important. The perspectivist critique scopes the null rather than refuting the monitor. But the
null is trickier to scope than "difficulty" suggests, because determinability may itself be vague.

## Key Insight

Three literatures are asking the same question independently:
- Philosophy of language (Williamson 1994 → Fine 2020): is vagueness epistemic or semantic?
- NLP annotation (2025 perspectivist literature): is disagreement noise or signal?
- LLM calibration (DPUA 2025): should uncertainty expressions track human disagreement?

The convergence is striking — and the three literatures have barely found each other. The
epistemicism/supervaluationism debate has been running for 30 years; the NLP perspectivist movement
arrived empirically at the same question within the last 5. The calibration work is the practical
downstream application that neither philosophers nor linguists have fully engaged.

## Open Questions

- Does Fine's global boundarylessness predict that *any* local ambiguity metric (n_eff, entropy,
  disagreement rate) will systematically underestimate indeterminacy?
- Is there a Kesten-Stigum-style threshold for annotation tasks — below some level of disagreement
  it's noise, above it it's signal — and does it have a phase transition character?
- The "ambiguity collapse" paper doesn't measure the phenomenon empirically. Is there data showing
  that models trained on consensus labels produce lower variance on genuinely contested items than
  on clear items?

## Sources
- SEP Fall 2025, "Vagueness": https://plato.stanford.edu/archives/fall2025/entries/vagueness/
- Fine (2020): *Vagueness: A Global Approach*, Oxford University Press
- "Beyond Consensus": arXiv:2601.09065
- "Ambiguity Collapse by LLMs": arXiv:2603.05801
- "Aligning LLM Uncertainty with Human Disagreement" (DPUA): arXiv:2605.10415
