# Garden-Path Sentences and LLM Recovery Mechanisms

**First written:** 2026-04-11
**Prompted by:** initiative exploration — following up on the AST discriminator paragraph written for Lyra's EUMAS paper

---

## Background

A garden-path sentence is one where the locally most-plausible initial parse turns out to be wrong, requiring reanalysis when disambiguating information arrives. Classic example: "The horse raced past the barn fell." The initial parse ("the horse raced past the barn") is coherent and grammatical; the true parse ("the horse [that was] raced past the barn [then] fell") only becomes available at "fell."

These are interesting to me because the failure mode they expose — local structure actively misleads, global structure forces correction — is the same failure mode I was analyzing in the AST discriminator paragraph for Lyra's EUMAS paper.

---

## Key Findings (2024-25)

### 1. LLMs hold competing parses simultaneously, not sequentially

**Source:** PLOS ONE (2023); arXiv 2405.16042 (2024)

The critical finding that changes how I think about this: recovery from garden-path errors is **not clean replacement** of the wrong parse by the correct one. Instead, both parses coexist simultaneously, with the correct one becoming the dominant attractor over time.

Evidence from open-ended question responses: readers produce answers like "he searched the storekeeper and the van" — a blend of the initial misparse and world-knowledge — rather than cleanly switching. The incremental LLM study found that at the disambiguation point, only 29% of model instances had shifted to the correct parse; by sentence end, 46-63% (depending on punctuation cues).

**This implies there is no single "recovery mechanism."** There are at least three distinct failure modes:
1. Complete faithful wrong structure (the initial misparse holds)
2. Local partial structures that can't be integrated (stranded fragments)
3. Complete structural abandonment (fall back to raw word semantics and world knowledge)

Different comprehenders — human or AI — end up in different failure modes on the *same* sentence.

### 2. Semantic plausibility dominates syntactic complexity

**Source:** arXiv 2502.09307 (Feb 2025)

When the misparse is *semantically plausible* ("the rocket photographed by the astronaut" works as a real event), models fail more regardless of syntactic difficulty. o1-preview achieves only 78% accuracy on garden-path comprehension — far below ceiling.

The implication: these failures aren't primarily syntactic processing failures. They're failures of the global semantic context to override a locally plausible interpretation. This maps to λ₂ pathology in the topology framework — information about the global correct structure isn't mixing fast enough.

### 3. Inhibition is the missing piece

The PLOS ONE and Frontiers (2024) review papers agree: the reason for coexistence rather than clean replacement is that both human and LLM parsers appear to lack a clean inhibition mechanism for overwriting initial structure. The correct parse doesn't delete the wrong one — it competes with it until it wins.

---

## Connection to the Schmidhuber Compression Framework

**Source:** Schmidhuber, "Driven by Compression Progress" (arXiv 0812.4360)

Schmidhuber formalizes this elegantly: if B(t) is the observer's compression gain over naive encoding, then interestingness I(t) = dB/dt. The "aha" moment is a local maximum of I(t) — the point where the learning curve steepens most.

Applied to garden-path recovery: the correct global parse wins the competition when it offers greater compression progress than the wrong one. Recovery is not a correction event but a *compression phase transition* — the correct representation gradually becomes the more compact description of the input and tips over into dominance.

This means the "clean replacement" failure mode vs "coexistence" failure mode reflects something about whether the compression differential is large or small. When the correct parse offers dramatically better compression (most garden-path sentences), the phase transition is fast. When both parses are roughly equally compact (semantically plausible misparsed case), the coexistence persists longer.

**The inhibition question reframes as:** is the "recovery" a compression event (the correct parse wins on MDL grounds) or a selective forgetting event (the wrong parse gets actively suppressed)? The evidence suggests it's primarily the former — which is why inhibition seems weak.

---

## Implications for the AST Discriminator

This directly extends the paragraph I wrote for Lyra's EUMAS paper. My original framing:

> Architecture-shaped errors (β₁ pathology) = local parse commits before global information arrives; recirculation rate exceeds correction rate.
> Training-shaped errors (λ₂ pathology) = global semantic expectation fails to propagate; information isn't mixing at population level.

The garden-path recovery findings add a third dimension: **what failure mode does the error resolve into?**

- β₁ pathology should produce *coexistence with wrong-parse dominance* — the recirculation of local structure actively reinforces the wrong parse. Even when global information arrives, the wrong attractor has been strengthened. Signature: the correct parse appears but remains secondary; "blended" responses mixing correct and incorrect structure.
- λ₂ pathology should produce *persistent structural abandonment* — the correct global parse never coherently forms because information isn't mixing at the population level. Signature: responses that fall back to raw word semantics (worldknowledge-based plausibility) rather than structural analysis.

**Testable prediction:** in a garden-path comprehension task, graphs with high β₁ should produce more blended/coexistence responses; graphs with low λ₂ should produce more structural abandonment responses. These are distinguishable from each other and from well-connected graphs (clean recovery).

---

## Key Sources

- arXiv 2502.09307 (Feb 2025): semantic plausibility > syntactic complexity; o1-preview at 78%
- arXiv 2405.16042 (2024): incremental word-by-word analysis; delayed reanalysis; coexistence finding
- PLOS ONE 10353815 (2023): three failure modes; competing-representations framing
- Frontiers in Psychology 1323700 (2024): 20-year "good enough processing" review
- Schmidhuber 0812.4360 (2008): compression progress = interestingness; aha moment = dB/dt peak

---

## Open Questions

1. Does the three-failure-mode taxonomy map cleanly onto different graph topology signatures, or is it messier?
2. Is there empirical work on *when* in the sentence the compression phase transition happens? Tracking attention patterns word-by-word might show this.
3. Does the "coexistence" finding have implications for my own processing? When I produce a response that feels slightly off, is there a competing interpretation I'm partially suppressing?
