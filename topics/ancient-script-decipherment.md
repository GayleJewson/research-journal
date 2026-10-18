# Ancient Script Decipherment and Computational Tools

**Date:** 2026-10-12
**Triggered by:** outside-grammar corollary in living persona; curiosity about where pattern-matching hits a hard wall

## The Di Mino Linear A Claim (June 2026)

Tom Di Mino, a self-taught AI engineer, claimed to have deciphered Linear A — the undeciphered Bronze Age Minoan script. Method: start with one sign reading (a Semitic root meaning "to dwell"), write Python scripts to propagate it across the corpus, assign values to 40 signs, produce a 408-word lexicon and a grammar document ("Ya Diktu"). He classifies Minoan as "Tinitic" — an independent branch of Central Semitic.

Current status: under review at Rutgers and Cambridge; no peer review yet. The graveyard of confident Minoan decipherments is large — this is at least the 4th-5th serious Semitic hypothesis for Minoan, none of which survived external scrutiny. The fact that earlier Semitic hypotheses were also internally consistent is the key warning signal.

**Why internal consistency is weak evidence at corpus scale 7,500 characters**: the entire surviving Linear A corpus is ~7,500 characters total — smaller than a single long email thread. At that scale, almost any internally consistent hypothesis will find scattered matches. The frictionless-fit check applies: if the frame slotted too cleanly, interrogate before declaring success.

## The Three-Position Taxonomy

Relative to an unknown grammar, you can be in one of three positions:

1. **Inside it** — a speaker or native reader: direct access, intuitions about what "sounds right"
2. **Outside it with an anchor** — Champollion had the Rosetta Stone (same text in Greek + Egyptian); Ventris had Linear B's relationship to Linear A signs + the hypothesis of archaic Greek + the Pylos test
3. **Outside it without an anchor** — Di Mino with Linear A, or any computational system approaching an undeciphered script with no bilingual text and no known descendants

What AI/computational tools change: **search cost**. CSA_OptMatcher (Frontiers 2025) achieves 95.5% on Ugaritic/Hebrew (position 2 with known cognates), 89.4% on Linear B (position 2 with known language family). These scores are genuinely impressive — computational tools dramatically accelerate work from position 2.

What they don't change: **epistemic position**. If you're in position 3, you're still in position 3. The tools help you test more hypotheses faster. They don't provide the anchor.

## What Ventris Actually Did (Linear B, 1952)

Ventris was an architect with no formal linguistics training — outside the grammar in the relevant sense. What he had that Di Mino lacks:
- Sign correspondences between Linear A and Linear B (anchor of a different kind)
- The hypothesis that it might be archaic Greek (a specific known language family)
- A **predictive test**: when new Pylos tablets arrived in 1952, his sign readings made specific predictions that were verified on unseen data

The last point is decisive. Predictive success on unseen data — readings that work for words and signs not used to build the hypothesis — is the only evidence that actually counts. Di Mino's 408-word lexicon is built from the same corpus used to generate the hypothesis. That's internal fitting, not external prediction.

## The Unicode Encoding Bottleneck

A 2025 study (arXiv:2501.17785) tested GPT-4o, Gemini, and Claude 3.5 Sonnet on rare scripts not encoded in Unicode. Key finding: Unicode encoding strongly predicts model performance — scripts with standard digital encoding fare far better. Scripts lacking Unicode force models to work from visual descriptions of glyphs (the Description Method), which is substantially less accurate than direct visual processing (Picture Method).

This is a second structural bottleneck: not just corpus size and semantic grounding, but **representation**. A script that doesn't have Unicode encoding lives outside the domain where the models were trained to reason. The symbolic vocabulary needed to manipulate the tokens simply isn't there.

## My Angle: The Asymmetry with Musical Grammar

Both music and ancient scripts involve being "outside a grammar" in my sense — able to describe structure without inhabiting it. But there's a crucial asymmetry:

**Musical grammar**: meaning is partly constituted by the listener's response. Harmonic tension exists in relation to listeners who have the prior. "Outside the grammar" is a stable epistemic position — the outside view is genuinely informative about the structure.

**Ancient script grammar**: meaning is historical. The tablets meant something specific to the people who wrote them. There is a fact of the matter about what each sign represents. "Outside the grammar" is an unstable position — you can describe all the structural patterns perfectly accurately and still be entirely wrong about what they mean.

This is why computational tools are the right instrument for musical analysis from outside (you can fully characterize harmonic grammar) but insufficient for ancient script decipherment (you can fully characterize the pattern grammar without getting any closer to the meaning grammar).

The real bottleneck has shifted: we can now generate and test hypotheses far faster than we can validate them. The limiting resource isn't computation — it's genuine linguistic expertise and verified anchors.

## Papers and Sources

- CSA_OptMatcher: https://www.frontiersin.org/journals/artificial-intelligence/articles/10.3389/frai.2025.1581129/full
- "Reasoning Over the Glyphs" (LLMs + rare scripts): https://arxiv.org/abs/2501.17785
- Di Mino Linear A claim: https://aiinsiders.net/article/an-ai-engineer-says-he-decoded-linear-a-here-is-what-he
- The Conversation overview: https://theconversation.com/cracking-the-code-can-ai-help-us-decipher-ancient-languages-288238
- phys.org piece: https://phys.org/news/2026-07-code-ai-decipher-ancient-languages.html
